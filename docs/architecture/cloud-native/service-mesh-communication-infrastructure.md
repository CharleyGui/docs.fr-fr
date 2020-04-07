---
title: Infrastructure de communication Service Mesh
description: Découvrez comment les technologies de maillage de service rationalisent la communication microservice native en nuage
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 8bb57e990dbf1baf8c246fe4aacfbb2904a251e6
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805753"
---
# <a name="service-mesh-communication-infrastructure"></a>Infrastructure de communication Service Mesh

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Tout au long de ce chapitre, nous avons exploré les défis de la communication microservice. Nous avons dit que les équipes de développement doivent être sensibles à la façon dont les services de back-end communiquent entre eux. Idéalement, moins il y a de communication interspède, mieux c’est. Cependant, l’évitement n’est pas toujours possible car les services back-end comptent souvent les uns sur les autres pour terminer leurs opérations.

Nous avons exploré différentes approches pour la mise en œuvre de la communication synchrone HTTP et de la messagerie asynchrone. Dans chacun des cas, le développeur est chargé d’implémenter le code de communication. Le code de communication est complexe et le temps intensif. Des décisions incorrectes peuvent entraîner d’importants problèmes de rendement.

Une approche plus moderne de la communication microservice autour d’une technologie nouvelle et en évolution rapide intitulée *Service Mesh*. Un [maillage de service](https://www.nginx.com/blog/what-is-a-service-mesh/) est une couche d’infrastructure configurable avec des capacités intégrées pour gérer la communication de service à service, la résilience, et de nombreuses préoccupations transversales. Il déplace la responsabilité de ces préoccupations hors des microservices et dans la couche de maillage de service. La communication est abstraite loin de vos microservices.

Un élément clé d’un maillage de service est un proxy. Dans une application cloud-native, un cas d’un proxy est généralement colocated avec chaque microservice. Bien qu’ils s’exécutent dans des processus distincts, les deux sont étroitement liés et partagent le même cycle de vie. Ce modèle, connu sous le nom [de modèle Sidecar](https://docs.microsoft.com/azure/architecture/patterns/sidecar), et est indiqué dans la figure 4-24.

![Maillage de service avec une voiture latérale](./media/service-mesh-with-side-car.png)

**Figure 4-24**. Maillage de service avec une voiture latérale

Notez dans le chiffre précédent comment les messages sont interceptés par un proxy qui fonctionne à côté de chaque microservice. Chaque proxy peut être configuré avec des règles de trafic spécifiques au microservice. Il comprend les messages et peut les acheminer à travers vos services et le monde extérieur.

En plus de gérer la communication service-service, le Service Mesh fournit un soutien pour la découverte de service et l’équilibrage de charge.

Une fois configuré, un maillage de service est très fonctionnel. Le maillage récupère un pool correspondant d’instances à partir d’un point de terminaison de découverte de service. Il envoie une demande à une instance de service spécifique, enregistrant le type de latence et de réponse du résultat. Il choisit l’instance la plus susceptible de renvoyer une réponse rapide en fonction de différents facteurs, y compris la latence observée pour les demandes récentes.

Un maillage de service gère les problèmes de trafic, de communication et de réseautage au niveau de l’application. Il comprend les messages et les demandes. Un maillage de service s’intègre généralement à un orchestrateur de conteneurs. Kubernetes prend en charge une architecture extensible dans laquelle un maillage de service peut être ajouté.

Dans le chapitre 6, nous plongeons profondément dans les technologies Service Mesh, y compris une discussion sur son architecture et les implémentations open-source disponibles.

## <a name="summary"></a>Résumé

Dans ce chapitre, nous avons discuté des modèles de communication cloud-native. Nous avons commencé par examiner comment les clients frontaux communiquent avec les microservices back-end. En cours de route, nous avons parlé des plates-formes API Gateway et de la communication en temps réel. Nous avons ensuite examiné comment les microservices communiquent avec d’autres services de back-end. Nous avons examiné à la fois la communication http://http synchrone et la messagerie asynchrone entre les services. Nous avons couvert gRPC, une technologie à venir dans le monde cloud-native. Enfin, nous avons introduit une nouvelle technologie en évolution rapide intitulée Service Mesh qui peut rationaliser la communication par microservices.

L’accent a été mis sur les services Azure gérés qui peuvent aider à mettre en œuvre la communication dans les systèmes cloud-natifs :

- [Passerelle d’application Azure](https://docs.microsoft.com/azure/application-gateway/overview)
- [Gestion des API Azure](https://azure.microsoft.com/services/api-management/)
- [Service Azure SignalR](https://azure.microsoft.com/services/signalr-service/)
- [Files d’attente Stockage Azure](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Grille d’événements Azure](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure Event Hub](https://azure.microsoft.com/services/event-hubs/)

Nous passons ensuite à distribuer des données dans des systèmes cloud-autochtones et les avantages et les défis qu’ils présentent.

### <a name="references"></a>References

- [.NET Microservices: Architecture for Containerized .NET applications](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Concevoir interservices communication pour les microservices](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Azure SignalR Service, un service entièrement géré pour ajouter des fonctionnalités en temps réel](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Contrôleur d’entrée Azure API Gateway](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [À propos de Ingress in Azure Kubernetes Service (AKS)](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [Documentation gRPC](https://grpc.io/docs/guides/)

- [gRPC pour les développeurs WCF](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [Comparaison des services gRPC avec http://APIs](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [Construire gRPC Services avec vidéo .NET](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[Suivant précédent](grpc.md)
>[Next](database-per-microservice.md)
