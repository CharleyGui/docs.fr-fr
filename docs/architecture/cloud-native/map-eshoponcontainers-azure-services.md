---
title: Mappage d’eShopOnContainers aux services Azure
description: Mappage de eShopOnContainers à des services Azure comme Azure Kubernetes service, API Gateway et Azure Service Bus.
ms.date: 05/13/2020
ms.openlocfilehash: c4627a4b6d9d8b62737984b507e638019544ab67
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400446"
---
# <a name="mapping-eshoponcontainers-to-azure-services"></a>Mappage d’eShopOnContainers aux services Azure

Bien que cela ne soit pas obligatoire, Azure est bien adapté à la prise en charge de eShopOnContainers, car le projet a été conçu pour être une application Cloud native. L’application est générée avec .NET Core, de sorte qu’elle peut s’exécuter sur des conteneurs Linux ou Windows en fonction de l’hôte de la station d’accueil. L’application est composée de plusieurs microservices autonomes, chacun avec ses propres données. Les différents microservices illustrent différentes approches, allant des simples opérations CRUD aux modèles DDD et CQRS plus complexes. Les microservices communiquent avec les clients via HTTP et les uns avec les autres via la communication basée sur les messages. L’application prend également en charge plusieurs plateformes pour les clients, dans la mesure où elle adopte HTTP comme protocole de communication standard et comprend des applications mobiles ASP.NET Core et Xamarin qui s’exécutent sur des plateformes Android, iOS et Windows.

L’architecture de l’application est illustrée dans la figure 2-5. À gauche, les applications clientes sont décomposées en versions mobiles, traditionnelles Web et d’application à page unique (SPA) Web. À droite se trouvent les composants côté serveur qui composent le système, qui peuvent chacun être hébergés dans des conteneurs et des clusters Kubernetes. L’application Web traditionnelle est alimentée par l’application ASP.NET Core MVC affichée en jaune. Cette application et les applications mobiles et Web SPA communiquent avec les microservices individuels par le biais d’une ou de plusieurs passerelles d’API. Les passerelles d’API suivent le modèle « principaux pour les serveurs frontaux » (BFF), ce qui signifie que chaque passerelle est conçue pour prendre en charge un client frontal donné. Les microservices individuels sont répertoriés à droite des passerelles d’API et incluent à la fois la logique métier et un magasin de persistance. Les différents services utilisent des bases de données SQL Server, des instances de cache Redims et des magasins MongoDB/CosmosDB. À l’extrême droite se trouve le bus d’événements du système, qui est utilisé pour la communication entre les microservices.

![eShopOnContainers architecture de la ](./media/eshoponcontainers-architecture.png)
 **figure 2-5**. L’architecture eShopOnContainers.

Les composants côté serveur de cette architecture sont tous mappés facilement aux services Azure.

## <a name="container-orchestration-and-clustering"></a>Orchestration et clustering de conteneur

Les services hébergés dans les conteneurs de l’application, du ASP.NET Core des applications MVC aux microservices de catalogue et de tri individuels, peuvent être hébergés et gérés dans Azure Kubernetes service (AKS). L’application peut s’exécuter localement sur docker et Kubernetes, et les mêmes conteneurs peuvent ensuite être déployés dans des environnements intermédiaires et de production hébergés dans AKS. Ce processus peut être automatisé comme nous le verrons dans la section suivante.

AKS fournit des services de gestion pour les clusters individuels de conteneurs. L’application déploie des conteneurs distincts pour chaque microservice dans le cluster AKS, comme indiqué dans le diagramme d’architecture ci-dessus. Cette approche permet à chaque service individuel d’évoluer indépendamment en fonction de ses besoins en ressources. Chaque microservice peut également être déployé indépendamment, et dans l’idéal, ces déploiements doivent entraîner un temps d’arrêt du système nul.

## <a name="api-gateway"></a>API Gateway

L’application eShopOnContainers a plusieurs clients frontaux et plusieurs services principaux différents. Il n’existe pas de correspondance un-à-un entre les applications clientes et les microservices qui les prennent en charge. Dans ce type de scénario, il peut y avoir une grande quantité de complexité lors de l’écriture du logiciel client pour l’interface avec les différents services principaux de manière sécurisée. Chaque client doit répondre à cette complexité de manière autonome, ce qui se traduit par une duplication et de nombreux emplacements dans lesquels des mises à jour sont mises à jour à mesure que les services changent ou que de nouvelles stratégies sont implémentées.

La gestion des API Azure (APIM) aide les organisations à publier des API de manière cohérente et gérable. APIM est constitué de trois composants : la passerelle d’API et le portail d’administration (le Portail Azure) et un portail des développeurs.

La passerelle d’API accepte les appels d’API et les achemine vers l’API principale appropriée. Il peut également fournir des services supplémentaires tels que la vérification des clés API ou des jetons JWT et la transformation d’API à la volée sans modification du code (par exemple, pour permettre aux clients d’attendre une interface plus ancienne).

Le Portail Azure est l’emplacement où vous définissez le schéma d’API et Empaquetez les différentes API dans les produits. Vous pouvez également configurer l’accès utilisateur, afficher des rapports et configurer des stratégies pour les quotas ou les transformations.

Le portail des développeurs fait office de ressource principale pour les développeurs. Il fournit aux développeurs une documentation sur les API, une console de test interactive et des rapports sur leur propre utilisation. Les développeurs utilisent également le portail pour créer et gérer leurs propres comptes, y compris l’abonnement et la prise en charge des clés d’API.

À l’aide de APIM, les applications peuvent exposer plusieurs groupes de services différents, chacun fournissant une back end pour un client frontal particulier. APIM est recommandé pour les scénarios complexes. Pour des besoins plus simples, vous pouvez utiliser la passerelle d’API légère ocelot. L’application eShopOnContainers utilise ocelot en raison de sa simplicité et elle peut être déployée dans le même environnement d’application que l’application elle-même. [En savoir plus sur eShopOnContainers, APIM et Ocelot.](../microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#azure-api-management)

Une autre option si votre application utilise AKS consiste à déployer le contrôleur d’entrée de la passerelle Azure en tant que Pod dans votre cluster AKS. Cela permet à votre cluster de s’intégrer à une passerelle de Azure Application, ce qui permet à la passerelle d’équilibrer la charge du trafic vers les Pod AKS. [En savoir plus sur le contrôleur d’entrée de la passerelle Azure pour AKS](https://github.com/Azure/application-gateway-kubernetes-ingress).

## <a name="data"></a>Données

Les différents services principaux utilisés par eShopOnContainers ont des exigences de stockage différentes. Plusieurs microservices utilisent SQL Server bases de données. Le microservice de panier utilise un cache Redims pour sa persistance. Le microservice d’emplacements attend une API MongoDB pour ses données. Azure prend en charge chacun de ces formats de données.

Pour la prise en charge des bases de données SQL Server, Azure propose des produits à partir de bases de données uniques jusqu’à des pools élastiques SQL Database hautement évolutifs. Des microservices individuels peuvent être configurés pour communiquer avec leurs propres bases de données SQL Serveres rapidement et facilement. Ces bases de données peuvent être mises à l’échelle si nécessaire pour prendre en charge chaque microservice distinct en fonction de ses besoins.

L’application eShopOnContainers stocke le panier d’achat actuel de l’utilisateur entre les demandes. Cela est géré par le microservice du panier qui stocke les données dans un cache ReDim. Dans le développement, ce cache peut être déployé dans un conteneur, alors qu’en production, il peut utiliser Azure cache pour les insertions. Le cache Azure pour les insertions est un service entièrement géré offrant des performances et une fiabilité élevées, sans qu’il soit nécessaire de déployer et de gérer vous-même des instances ou des conteneurs ReDim.

Le microservice d’emplacements utilise une base de données NoSQL MongoDB pour sa persistance. Pendant le développement, la base de données peut être déployée dans son propre conteneur, alors qu’en production, le service peut tirer parti de l' [API de Azure Cosmos DB pour MongoDB](/azure/cosmos-db/mongodb-introduction). L’un des avantages de Azure Cosmos DB est sa capacité à exploiter plusieurs protocoles de communication, notamment une API SQL et des API NoSQL courantes, notamment MongoDB, Cassandra, Gremlin et le stockage de tables Azure. Azure Cosmos DB offre une base de données entièrement gérée et distribuée à l’échelle mondiale en tant que service qui peut évoluer pour répondre aux besoins des services qui l’utilisent.

Les données distribuées dans les applications Cloud natives sont abordées plus en détail dans le [Chapitre 5](distributed-data.md).

## <a name="event-bus"></a>Bus d’événements

L’application utilise des événements pour communiquer les modifications entre les différents services. Cette fonctionnalité peut être implémentée avec diverses implémentations, et l’application eShopOnContainers utilise localement l' [RabbitMQ](https://www.rabbitmq.com/). Lorsqu’elle est hébergée dans Azure, l’application peut tirer parti de [Azure Service bus](/azure/service-bus/) pour sa messagerie. Azure Service Bus est un courtier de messages d’intégration entièrement géré qui permet aux applications et aux services de communiquer entre eux de manière asynchrone, fiable et asynchrone. Azure Service Bus prend en charge les files d’attente individuelles ainsi que des *rubriques* distinctes pour prendre en charge les scénarios de serveur de publication et d’abonné. L’application eShopOnContainers s’appuie sur des rubriques avec Azure Service Bus pour prendre en charge la distribution de messages d’un microservice à un autre microservice qui devait réagir à un message donné.

## <a name="resiliency"></a>Résilience

Une fois déployé en production, l’application eShopOnContainers peut tirer parti de plusieurs services Azure disponibles pour améliorer sa résilience. L’application publie des contrôles d’intégrité, qui peuvent être intégrés à Application Insights pour fournir des rapports et des alertes en fonction de la disponibilité de l’application. Les ressources Azure fournissent également des journaux de diagnostic qui peuvent être utilisés pour identifier et corriger les bogues et les problèmes de performances. Les journaux de ressources fournissent des informations détaillées sur le moment et la façon dont les différentes ressources Azure sont utilisées par l’application. Vous en apprendrez davantage sur les fonctionnalités de résilience native du Cloud dans le [chapitre 6](resiliency.md).

>[!div class="step-by-step"]
>[Précédent](introduce-eshoponcontainers-reference-app.md) 
> [Suivant](deploy-eshoponcontainers-azure.md)
