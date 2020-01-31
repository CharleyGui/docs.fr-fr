---
title: Infrastructure de communication Service Mesh
description: En savoir plus sur la façon dont les technologies de maillage de service rationalisent la communication des microservices natives Cloud
author: robvet
ms.date: 09/10/2019
ms.openlocfilehash: 66bc69580cc56efe725683c16a047aeb07e7e840
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76780935"
---
# <a name="service-mesh-communication-infrastructure"></a>Infrastructure de communication Service Mesh

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Tout au long de ce chapitre, nous avons exploré les défis liés à la communication des microservices. Nous avons dit que les équipes de développement doivent être sensibles à la façon dont les services principaux communiquent entre eux. Dans l’idéal, la communication entre les services est moins efficace. Toutefois, l’évitement n’est pas toujours possible, car les services principaux s’appuient souvent les uns sur les autres pour effectuer des opérations.

Nous avons exploré différentes approches pour implémenter une communication HTTP synchrone et une messagerie asynchrone. Dans chacun des cas, le développeur est chargé d’implémenter le code de communication. Le code de communication est complexe et fastidieux. Des décisions incorrectes peuvent entraîner des problèmes de performances significatifs.

Une approche plus moderne des centres de communication des microservices autour d’une technologie nouvelle et en constante évolution, intitulée *maille du service*. Une [maille de service](https://www.nginx.com/blog/what-is-a-service-mesh/) est une couche d’infrastructure configurable avec des fonctionnalités intégrées pour gérer la communication entre les services, la résilience et de nombreux problèmes transversaux. Il déplace la responsabilité de ces problèmes sur les microservices et dans la couche de maillage de service. La communication est extraite de vos microservices.

Un composant clé d’une maille de service est un proxy. Dans une application Cloud native, une instance d’un proxy est généralement colocalisée avec chaque microservice. Bien qu’ils s’exécutent dans des processus distincts, les deux sont étroitement liés et partagent le même cycle de vie. Ce modèle, connu sous le nom de [modèle de side-car](https://docs.microsoft.com/azure/architecture/patterns/sidecar), est illustré à la figure 4-23.

![Maille de service avec une voiture latérale](./media/service-mesh-with-side-car.png)

**Figure 4-23**. Maille de service avec une voiture latérale

Notez dans la figure précédente Comment les messages sont interceptés par un proxy qui s’exécute parallèlement à chaque microservice. Chaque proxy peut être configuré avec des règles de trafic spécifiques au microservice. Il comprend les messages et peut les acheminer entre vos services et le monde extérieur.

En plus de la gestion de la communication de service à service, la maille de service prend en charge la découverte de service et l’équilibrage de charge.

Une fois configuré, un maillage de service est très fonctionnel. La maille récupère un pool d’instances correspondant à partir d’un point de terminaison de découverte de service. Il envoie une demande à une instance de service spécifique, en enregistrant la latence et le type de réponse du résultat. Il choisit l’instance la plus susceptible de retourner une réponse rapide en fonction de différents facteurs, y compris la latence observée pour les demandes récentes.

Un maillage de service gère le trafic, la communication et les problèmes de mise en réseau au niveau de l’application. Il comprend les messages et les demandes. Une maille de service s’intègre généralement avec un orchestrateur de conteneur. Kubernetes prend en charge une architecture extensible dans laquelle un maillage de service peut être ajouté.

Dans le chapitre 6, nous explorons en profondeur les technologies de maille de service, y compris une discussion sur son architecture et les implémentations Open source disponibles.

## <a name="summary"></a>Récapitulatif

Dans ce chapitre, nous avons abordé les modèles de communication natifs dans le Cloud. Nous avons commencé par examiner comment les clients frontaux communiquent avec les microservices back-end. En cours de route, nous avons parlé des plateformes de passerelle d’API et de la communication en temps réel. Nous avons ensuite vu comment les microservices communiquent avec d’autres services principaux. Nous avons examiné la communication HTTP synchrone et la messagerie asynchrone entre les services. Nous avons abordé gRPC, une technologie à venir dans le monde Cloud-native. Enfin, nous avons introduit une nouvelle technologie en constante évolution, intitulée Service Mesh, qui permet de rationaliser la communication des microservices.

Une mise en évidence spéciale s’est produite sur les services Azure gérés qui peuvent aider à implémenter la communication dans les systèmes natifs du Cloud :

- [Passerelle Azure Application](https://docs.microsoft.com/azure/application-gateway/overview)
- [Gestion des API Azure](https://azure.microsoft.com/services/api-management/)
- [Service Azure SignalR](https://azure.microsoft.com/services/signalr-service/)
- [Files d’attente de stockage Azure](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview)
- [Hub d’événements Azure](https://azure.microsoft.com/services/event-hubs/)

Nous allons ensuite passer aux données distribuées dans les systèmes natifs du Cloud et aux avantages et défis qu’il présente.

### <a name="references"></a>Références

- [Microservices .NET : architecture pour les applications .NET en conteneur](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Conception de la communication interservice pour les microservices](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Service Azure Signalr, service entièrement géré pour l’ajout de fonctionnalités en temps réel](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Contrôleur d’entrée de la passerelle API Azure](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [À propos de l’entrée dans Azure Kubernetes service (AKS)](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [GRPC pratique](https://www.worldcat.org/title/practical-grpc/oclc/1042342319)

- [Documentation gRPC](https://grpc.io/docs/guides/)

- [gRPC pour les développeurs WCF](https://bing.com) [Mark gRPC]

- [Comparaison des services gRPC avec les API HTTP](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

>[!div class="step-by-step"]
>[Précédent](rest-grpc.md)
>[Suivant](Database-per-microservice.md)
