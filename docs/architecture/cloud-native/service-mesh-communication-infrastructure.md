---
title: Infrastructure de communication Service Mesh
description: En savoir plus sur la façon dont les technologies de maillage de service rationalisent la communication des microservices natives Cloud
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 39dc1ded06eb0b92a2a1b40cfe981d9bd49bf381
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165947"
---
# <a name="service-mesh-communication-infrastructure"></a>Infrastructure de communication Service Mesh

Tout au long de ce chapitre, nous avons exploré les défis liés à la communication des microservices. Nous avons dit que les équipes de développement doivent être sensibles à la façon dont les services principaux communiquent entre eux. Dans l’idéal, la communication entre les services est moins efficace. Toutefois, l’évitement n’est pas toujours possible, car les services principaux s’appuient souvent les uns sur les autres pour effectuer des opérations.

Nous avons exploré différentes approches pour implémenter une communication HTTP synchrone et une messagerie asynchrone. Dans chacun des cas, le développeur est chargé d’implémenter le code de communication. Le code de communication est complexe et fastidieux. Des décisions incorrectes peuvent entraîner des problèmes de performances significatifs.

Une approche plus moderne des centres de communication des microservices autour d’une technologie nouvelle et en constante évolution, intitulée *maille du service*. Une [maille de service](https://www.nginx.com/blog/what-is-a-service-mesh/) est une couche d’infrastructure configurable avec des fonctionnalités intégrées pour gérer la communication entre les services, la résilience et de nombreux problèmes transversaux. Il déplace la responsabilité de ces problèmes sur les microservices et dans la couche de maillage de service. La communication est extraite de vos microservices.

Un composant clé d’une maille de service est un proxy. Dans une application Cloud native, une instance d’un proxy est généralement colocalisée avec chaque microservice. Bien qu’ils s’exécutent dans des processus distincts, les deux sont étroitement liés et partagent le même cycle de vie. Ce modèle, connu sous le nom de [modèle de side-car](/azure/architecture/patterns/sidecar), est illustré à la figure 4-24.

![Maille de service avec une voiture latérale](./media/service-mesh-with-side-car.png)

**Figure 4-24**. Maille de service avec une voiture latérale

Notez dans la figure précédente Comment les messages sont interceptés par un proxy qui s’exécute parallèlement à chaque microservice. Chaque proxy peut être configuré avec des règles de trafic spécifiques au microservice. Il comprend les messages et peut les acheminer entre vos services et le monde extérieur.

En plus de la gestion de la communication de service à service, la maille de service prend en charge la découverte de service et l’équilibrage de charge.

Une fois configuré, un maillage de service est très fonctionnel. La maille récupère un pool d’instances correspondant à partir d’un point de terminaison de découverte de service. Il envoie une demande à une instance de service spécifique, en enregistrant la latence et le type de réponse du résultat. Il choisit l’instance la plus susceptible de retourner une réponse rapide en fonction de différents facteurs, y compris la latence observée pour les demandes récentes.

Un maillage de service gère le trafic, la communication et les problèmes de mise en réseau au niveau de l’application. Il comprend les messages et les demandes. Une maille de service s’intègre généralement avec un orchestrateur de conteneur. Kubernetes prend en charge une architecture extensible dans laquelle un maillage de service peut être ajouté.

Dans le chapitre 6, nous explorons en profondeur les technologies de maille de service, y compris une discussion sur son architecture et les implémentations Open source disponibles.

## <a name="summary"></a>Résumé

Dans ce chapitre, nous avons abordé les modèles de communication natifs dans le Cloud. Nous avons commencé par examiner comment les clients frontaux communiquent avec les microservices back-end. En cours de route, nous avons parlé des plateformes de passerelle d’API et de la communication en temps réel. Nous avons ensuite vu comment les microservices communiquent avec d’autres services principaux. Nous avons examiné la communication HTTP synchrone et la messagerie asynchrone entre les services. Nous avons abordé gRPC, une technologie à venir dans le monde Cloud-native. Enfin, nous avons introduit une nouvelle technologie en constante évolution, intitulée Service Mesh, qui permet de rationaliser la communication des microservices.

Une mise en évidence spéciale s’est produite sur les services Azure gérés qui peuvent aider à implémenter la communication dans les systèmes natifs du Cloud :

- [Application Gateway Azure](/azure/application-gateway/overview)
- [Gestion des API Azure](https://azure.microsoft.com/services/api-management/)
- [Azure SignalR Service](https://azure.microsoft.com/services/signalr-service/)
- [Files d’attente Stockage Azure](/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Event Grid](/azure/event-grid/overview)
- [Azure Event Hub](https://azure.microsoft.com/services/event-hubs/)

Nous allons ensuite passer aux données distribuées dans les systèmes natifs du Cloud et aux avantages et défis qu’il présente.

### <a name="references"></a>Références

- [Microservices .NET : architecture pour les applications .NET en conteneur](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Conception de la communication interservice pour les microservices](/azure/architecture/microservices/design/interservice-communication)

- [Service Azure Signalr, service entièrement géré pour l’ajout de fonctionnalités en temps réel](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Contrôleur d’entrée de la passerelle API Azure](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [À propos de l’entrée dans Azure Kubernetes service (AKS)](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [Documentation gRPC](https://grpc.io/docs/guides/)

- [gRPC pour les développeurs WCF](../grpc-for-wcf-developers/index.md)

- [Comparaison des services gRPC avec les API HTTP](/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [Génération de services gRPC avec la vidéo .NET](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[Précédent](grpc.md) 
> [Suivant](distributed-data.md)
