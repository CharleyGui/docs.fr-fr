---
title: Implémentation de la communication basée sur les événements entre les microservices (événements d’intégration)
description: Architecture des microservices .NET pour les applications .NET conteneurisées | Comprendre les événements d’intégration pour implémenter la communication basée sur les événements entre les microservices.
ms.date: 10/02/2018
ms.openlocfilehash: a778acba3e17b084840b77d903533f9180ca01d9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91152531"
---
# <a name="implementing-event-based-communication-between-microservices-integration-events"></a>Implémentation de la communication basée sur les événements entre les microservices (événements d’intégration)

Comme décrit précédemment, quand vous utilisez la communication basée sur les événements, un microservice publie un événement chaque fois qu’une chose notable se produit (par exemple, lorsqu’une entité commerciale est mise à jour). Les autres microservices s’abonnent à ces événements. Lorsqu’un microservice reçoit un événement, il peut mettre à jour ses propres entités commerciales, ce qui peut générer la publication d’autres événements. Il s’agit de l’essence même du concept de cohérence éventuelle. Ce système de publication/abonnement est généralement obtenu à l’aide de l’implémentation d’un bus d’événements. Le bus d’événements peut être conçu comme l’interface de l’API nécessaire pour s’abonner aux événements et s’en désabonner, ainsi que pour les publier. Il peut également avoir une ou plusieurs implémentations basées sur une communication entre processus ou une communication de messagerie, telle qu’une file d’attente de messagerie ou un bus de service prenant en charge la communication asynchrone, ainsi qu’un modèle de publication/abonnement.

Vous pouvez utiliser des événements pour implémenter des transactions commerciales concernant plusieurs services, et ainsi obtenir une cohérence à terme entre ces services. Une transaction cohérente à terme se compose d’une série d’actions distribuées. À chaque action, le microservice met à jour une entité commerciale et publie un événement qui déclenche l’action suivante. La figure 6-18 ci-dessous montre un événement PriceUpdated publié par le biais d’un bus d’événements, ce qui signifie que la mise à jour du prix est propagée vers le panier et d’autres microservices.

![Diagramme de communication asynchrone pilotée par les événements avec un bus d’événements.](./media/integration-event-based-microservice-communications/event-driven-communication.png)

**Figure 6-18.** Communication pilotée par les événements et basée sur un bus d’événements

Cette section explique comment implémenter ce type de communication avec .NET à l’aide d’une interface de bus d’événements générique, comme indiqué dans la figure 6-18. Il existe plusieurs implémentations possibles, qui utilisent chacune leur propre technologie ou infrastructure, telles que RabbitMQ, Azure Service Bus ou tout autre Service Bus tiers open source ou commercial.

## <a name="using-message-brokers-and-services-buses-for-production-systems"></a>Utilisation de répartiteurs de messages et de bus de services pour les systèmes de production

Comme indiqué dans la section relative à l’architecture, vous pouvez choisir parmi plusieurs technologies de messagerie pour l’implémentation de votre bus d’événements abstraits. Toutefois, ces technologies sont situées à des niveaux différents. Par exemple, le répartiteur de messages RabbitMQ se trouve à un niveau inférieur à celui des produits commerciaux tels qu’Azure Service Bus, NServiceBus, MassTransit ou Brighter. La plupart de ces produits peuvent fonctionner par-dessus RabbitMQ ou Azure Service Bus. Vous devez choisir le produit en fonction du nombre de fonctionnalités et du niveau de scalabilité prête à l’emploi dont vous avez besoin pour votre application.

Si vous souhaitez uniquement implémenter une preuve de concept de bus d’événements pour votre environnement de développement, comme dans l’exemple eShopOnContainers, une simple implémentation par-dessus RabbitMQ exécutée dans un conteneur peut être suffisante. Toutefois, pour les systèmes stratégiques et les systèmes de production qui nécessitent un haut niveau de scalabilité, il peut être utile d’évaluer et d’utiliser Azure Service Bus.

Si vous avez besoin d’un haut niveau d’abstraction et de fonctionnalités plus riches telles que [Sagas](https://docs.particular.net/nservicebus/sagas/) pour les processus longs qui facilitent le développement distribué, d’autres bus de services commerciaux et open source comme NServiceBus, MassTransit et Brighter méritent d’être évalués. Dans ce cas, les abstractions et l’API à utiliser sont généralement celles fournies par ces bus de services de haut niveau, et non vos propres abstractions (comme les [abstractions de bus d’événements simples fournies dans eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/BuildingBlocks/EventBus/EventBus/Abstractions/IEventBus.cs)). Pour ce faire, vous pouvez rechercher les [eShopOnContainers dupliqués à l’aide de NServiceBus](https://go.particular.net/eShopOnContainers) (exemple dérivé supplémentaire implémenté par un logiciel particulier).

Bien sûr, vous pourriez toujours créer vos propres fonctionnalités service bus sur des technologies de niveau inférieur telles que RabbitMQ et docker, mais le travail nécessaire pour « réinventer la roue » peut être trop coûteux pour une application d’entreprise personnalisée.

Pour réitérer : les exemples d’abstractions de bus d’événements et d’implémentation présentés dans l’exemple eShopOnContainers sont destinés à être utilisés uniquement comme preuve de concept. Une fois que vous avez décidé que vous souhaitez établir une communication asynchrone et pilotée par les événements, comme expliqué dans la section actuelle, vous devez choisir le produit Service Bus qui convient le mieux à vos besoins pour la production.

## <a name="integration-events"></a>Événements d’intégration

Les événements d’intégration sont utilisés pour synchroniser l’état du domaine sur plusieurs microservices ou systèmes externes. Pour cela, vous devez publier les événements d’intégration en dehors du microservice. Lorsqu’un événement est publié sur plusieurs microservices récepteurs (sur tous les microservices abonnés à l’événement d’intégration), le gestionnaire d’événements de chaque microservice récepteur gère l’événement.

Un événement d’intégration est essentiellement une classe conteneur de données, comme le montre l’exemple suivant :

```csharp
public class ProductPriceChangedIntegrationEvent : IntegrationEvent
{
    public int ProductId { get; private set; }
    public decimal NewPrice { get; private set; }
    public decimal OldPrice { get; private set; }

    public ProductPriceChangedIntegrationEvent(int productId, decimal newPrice,
        decimal oldPrice)
    {
        ProductId = productId;
        NewPrice = newPrice;
        OldPrice = oldPrice;
    }
}
```

Les événements d’intégration peuvent être définis au niveau de l’application de chaque microservice. De cette façon, ils sont dissociés des autres microservices, d’une manière comparable à la façon dont les ViewModels sont définis sur le serveur et sur le client. Cependant, il n’est pas recommandé de partager une bibliothèque d’événements d’intégration entre plusieurs microservices, car cela aurait pour effet de coupler ces microservices avec une seule bibliothèque de données de définition d’événements. Un tel partage est déconseillé, tout comme le partage d’un modèle de domaine entre plusieurs microservices, car les microservices doivent être complètement autonomes.

Seules certaines bibliothèques peuvent être partagées entre plusieurs microservices. Parmi elles figurent les bibliothèques qui sont des blocs d’application finale, comme [l’API cliente Event Bus](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/BuildingBlocks/EventBus) de l’exemple eShopOnContainers. Vous avez également les bibliothèques qui constituent des outils pouvant être partagés en tant que composants NuGet, comme les sérialiseurs JSON.

## <a name="the-event-bus"></a>Le bus d’événements

Un bus d’événements permet une communication de type publication/abonnement entre les microservices, sans nécessiter que les composants soient explicitement informés de la présence des uns des autres, comme le montre la figure 6-19.

![Diagramme montrant le modèle de publication/d’abonnement de base.](./media/integration-event-based-microservice-communications/publish-subscribe-basics.png)

**Figure 6-19.** Principes de base de la communication de type publication/abonnement avec un bus d’événements

Le diagramme ci-dessus montre que le microservice A effectue une publication sur le bus d’événements, qui distribue aux microservices B et C d’abonnement, sans que le serveur de publication doive connaître les abonnés. Le bus d’événements est lié au modèle Observateur et au modèle Publication/Abonnement.

### <a name="observer-pattern"></a>Modèle Observateur

Dans le [modèle Observateur](https://en.wikipedia.org/wiki/Observer_pattern), votre objet principal (l’observable) envoie aux autres objets intéressés (les observateurs) des informations pertinentes (des événements).

### <a name="publishsubscribe-pubsub-pattern"></a>Modèle Publication/Abonnement

L’objectif du [modèle Publication/Abonnement](/previous-versions/msp-n-p/ff649664(v=pandp.10)) est le même que celui du modèle Observateur, c’est-à-dire que vous souhaitez informer les autres services de certains événements. Toutefois, il existe une différence importante entre ces deux modèles. Dans le modèle d’observateur, la diffusion est effectuée directement à partir de l’observable vers les observateurs, de sorte qu’ils se « identifient » les uns les autres. En revanche, lorsque vous utilisez un modèle Publication/Abonnement, un troisième élément est impliqué. Il s’agit du répartiteur (de messages) ou du bus d’événements, qui est connu à la fois de celui qui publie et de celui qui s’abonne. Par conséquent, lorsque vous utilisez le modèle Publication/Abonnement, celui qui publie et ses abonnés sont dissociés grâce au bus d’événements ou au répartiteur de messages.

### <a name="the-middleman-or-event-bus"></a>L’intermédiaire ou le bus d’événements

Comment permettre l’anonymat entre celui qui publie les événements et ses abonnés ? Un moyen simple consiste à laisser un intermédiaire s’occuper de toutes les communications. Un bus d’événements joue le rôle de cet intermédiaire.

Un bus d’événements est généralement constitué de deux parties :

- L’abstraction ou interface

- Une ou plusieurs implémentations

Dans la figure 6-19, vous pouvez voir que, du point de vue d’une application, le bus d’événements n’est autre qu’un canal de publication/abonnement. La façon dont vous implémentez cette communication asynchrone peut varier. Plusieurs implémentations sont possibles, de sorte que vous pouvez passer de l’une à l’autre, selon les exigences de votre environnement (par exemple, s’il s’agit d’un environnement de production ou d’un environnement de développement).

Dans la figure 6-20, vous pouvez voir une abstraction d’un bus d’événements avec plusieurs implémentations basées sur des technologies de messagerie d’infrastructure, telles que RabbitMQ, Azure Service Bus ou un autre répartiteur de messages/événements.

![Diagramme montrant l’ajout d’une couche d’abstraction de bus d’événements.](./media/integration-event-based-microservice-communications/multiple-implementations-event-bus.png)

**Figure 6-20.** Les différentes implémentations d’un bus d’événements

Il est judicieux de définir le bus d’événements par le biais d’une interface, pour pouvoir l’implémenter avec plusieurs technologies comme RabbitMQ Azure Service Bus ou autre. Toutefois, comme mentionné précédemment, l’utilisation de vos propres abstractions (l’interface du bus d’événements) convient uniquement si vous avez besoin de fonctionnalités de bus d’événements de base, prises en charge par vos abstractions. Si vous avez besoin de fonctionnalités de bus de services plus riches, utilisez l’API et les abstractions fournies par votre bus de services commercial préféré, plutôt que vos propres abstractions.

### <a name="defining-an-event-bus-interface"></a>Définition de l’interface d’un bus d’événements

Commençons par un code d’implémentation pour l’interface du bus d’événements et des implémentations possibles à des fins d’exploration. L’interface doit être générique et simple, comme celle qui suit.

```csharp
public interface IEventBus
{
    void Publish(IntegrationEvent @event);

    void Subscribe<T, TH>()
        where T : IntegrationEvent
        where TH : IIntegrationEventHandler<T>;

    void SubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void UnsubscribeDynamic<TH>(string eventName)
        where TH : IDynamicIntegrationEventHandler;

    void Unsubscribe<T, TH>()
        where TH : IIntegrationEventHandler<T>
        where T : IntegrationEvent;
}
```

La méthode `Publish` est simple. Le bus d’événements va diffuser l’événement d’intégration qui lui a été passé à tous les microservices, et même aux applications externes, abonnées à cet événement. Cette méthode est utilisée par le microservice qui publie l’événement.

Les méthodes `Subscribe` (vous pouvez avoir plusieurs implémentations selon les arguments) sont utilisées par les microservices qui souhaitent recevoir des événements. Cette méthode a deux arguments. Le premier est l’événement d’intégration auquel s’abonner (`IntegrationEvent`). Le deuxième argument est le gestionnaire d’événements d’intégration (ou méthode de rappel) nommé `IIntegrationEventHandler<T>`, qui doit être exécuté lorsque le microservice récepteur obtient le message d’événement d’intégration.

## <a name="additional-resources"></a>Ressources supplémentaires

Certaines solutions de messagerie prêtes pour la production :

- **Azure Service Bus** \
  <https://docs.microsoft.com/azure/service-bus-messaging/>
  
- **NServiceBus** \
  <https://particular.net/nservicebus>
  
- **MassTransit** \
  <https://masstransit-project.com/>

> [!div class="step-by-step"]
> [Précédent](database-server-container.md) 
>  [Suivant](rabbitmq-event-bus-development-test-environment.md)
