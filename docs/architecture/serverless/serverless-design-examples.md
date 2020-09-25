---
title: Exemples de conception sans serveur-applications sans serveur
description: Comprenez les différents scénarios pris en charge par les architectures sans serveur, de la planification et du traitement basé sur les événements aux déclencheurs de fichiers et au processus de flux.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3aa9b7951fd8f11a65a64c22443de7041aba7d94
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171752"
---
# <a name="serverless-design-examples"></a>Exemples de conceptions serverless

Il existe de nombreux modèles de conception pour les serveurs. Cette section capture certains scénarios courants qui utilisent sans serveur. Tous les exemples ont en commun la combinaison fondamentale d’un déclencheur d’événements et d’une logique métier.

## <a name="scheduling"></a>Planification

La planification de tâches est une fonction courante. Le diagramme suivant montre une base de données héritée qui ne dispose pas de vérifications d’intégrité appropriées. La base de données doit être nettoyée régulièrement. La fonction sans serveur recherche des données non valides et les nettoie. Le déclencheur est un minuteur qui exécute le code selon une planification.

![Planification sans serveur](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Séparation des responsabilités en matière de commande et de requête (CQRS)

Séparation des responsabilités en matière de commande et de requête (CQRS) est un modèle qui fournit des interfaces différentes pour la lecture (ou l’interrogation) des données et des opérations qui modifient les données. Elle résout plusieurs problèmes courants. Dans les systèmes CRUD (Read Update Update) traditionnels, les conflits peuvent provenir d’un grand nombre de lectures et d’écritures dans le même magasin de données. Le verrouillage peut se produire fréquemment et ralentir considérablement les lectures. Souvent, les données sont présentées sous la forme d’un composite de plusieurs objets de domaine et les opérations de lecture doivent combiner des données provenant de différentes entités.

À l’aide de CQRS, une lecture peut impliquer une entité « aplatie » spéciale qui modélise les données de la manière dont elles sont consommées. La lecture est gérée différemment de la façon dont il est stocké. Par exemple, bien que la base de données puisse stocker un contact comme un enregistrement d’en-tête avec un enregistrement d’adresse enfant, la lecture peut impliquer une entité avec les propriétés d’en-tête et d’adresse. Il existe de nombreuses approches pour créer le modèle de lecture. Elle peut être matérialisée à partir de vues. Les opérations de mise à jour peuvent être encapsulées en tant qu’événements isolés qui déclenchent ensuite des mises à jour vers deux modèles différents. Des modèles distincts existent pour la lecture et l’écriture.

![CQRS, exemple](./media/cqrs-example.png)

Sans serveur peut prendre en charge le modèle CQRS en fournissant les points de terminaison séparés. Une fonction sans serveur prend en charge les requêtes ou les lectures, et une fonction ou un ensemble de fonctions sans serveur différentes gère les opérations de mise à jour. Une fonction sans serveur peut également être chargée de maintenir à jour le modèle de lecture et peut être déclenchée par le [flux de modification](/azure/cosmos-db/change-feed)de la base de données. Le développement frontal est simplifié pour la connexion aux points de terminaison nécessaires. Le traitement des événements est géré sur le back end. Ce modèle est également adapté aux projets volumineux, car les différentes équipes peuvent travailler sur différentes opérations.

## <a name="event-based-processing"></a>Traitement basé sur les événements

Dans les systèmes basés sur des messages, les événements sont souvent collectés dans les files d’attente ou dans les rubriques sur les éditeurs/abonnés à utiliser. Ces événements peuvent déclencher des fonctions sans serveur pour exécuter une partie de la logique métier. Les systèmes à base d’événements sont un exemple de traitement basé sur les événements. Un « événement » est déclenché pour marquer une tâche comme terminée. Une fonction sans serveur déclenchée par l’événement met à jour le document de base de données approprié. Une deuxième fonction sans serveur peut utiliser l’événement pour mettre à jour le modèle de lecture pour le système. [Azure Event Grid](/azure/event-grid/overview) permet d’intégrer des événements avec les fonctions en tant qu’abonnés.

> Les événements sont des messages d’information. Pour plus d’informations, consultez [modèle d’approvisionnement en événements](/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Transformations et déclencheurs de fichiers

L’extraction, la transformation et le chargement (ETL) est une fonction métier courante. Sans serveur est une solution idéale pour ETL, car elle permet le déclenchement du code dans le cadre d’un pipeline. Des composants de code individuels peuvent répondre à différents aspects. Une fonction sans serveur peut télécharger le fichier, une autre applique la transformation et une autre charge les données. Le code peut être testé et déployé indépendamment, ce qui facilite la maintenance et la mise à l’échelle lorsque cela est nécessaire.

![Transformations et déclencheurs de fichiers sans serveur](./media/serverless-file-triggers.png)

Dans le diagramme, « stockage froid » fournit des données qui sont analysées dans [Azure Stream Analytics](/azure/stream-analytics). Tout problème rencontré dans le flux de données déclenche une fonction Azure pour traiter l’anomalie.

## <a name="asynchronous-background-processing-and-messaging"></a>Traitement et messagerie en arrière-plan asynchrone

La messagerie asynchrone et le traitement en arrière-plan permettent aux applications de lancer des processus sans avoir à attendre. Une application OCR est un exemple de traitement asynchrone. Une image est envoyée et mise en file d’attente pour traitement. L’analyse de l’image pour extraire du texte peut prendre du temps, et une fois qu’elle est terminée, une notification est envoyée. Sans serveur peut gérer à la fois l’appel et le résultat dans ce scénario.

## <a name="web-apps-and-apis"></a>API et applications web

Un scénario courant pour les applications sans serveur est la plupart des applications multicouches, généralement celles où la couche d’interface utilisateur est une application Web. La popularité des applications à page unique (SPA) a récemment rencontré des pics. Les applications SPA affichent une seule page, puis reposent sur les appels d’API et les données retournées pour afficher dynamiquement une nouvelle interface utilisateur sans recharger une page entière. Le rendu côté client offre une application beaucoup plus rapide et plus réactive à l’utilisateur final.

Les points de terminaison sans serveur déclenchés par des appels HTTP peuvent être utilisés pour gérer les demandes d’API. Par exemple, une société ad services peut appeler une fonction sans serveur avec des informations de profil utilisateur pour demander une publicité personnalisée. La fonction sans serveur retourne la publicité personnalisée et la page Web la restitue.

![API Web sans serveur](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Pipeline de données

Les fonctions sans serveur peuvent être utilisées pour faciliter un pipeline de données. Dans cet exemple, un fichier déclenche une fonction pour convertir les données d’un fichier CSV en lignes de données dans une table. La table organisée permet à un Power BI tableau de bord de présenter des analyses à l’utilisateur final.

![Pipeline de données sans serveur](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Traitement des flux de données

Les appareils et les capteurs génèrent souvent des flux de données qui doivent être traités en temps réel. Il existe un certain nombre de technologies qui peuvent capturer des messages et des flux de [Event hubs](/azure/event-hubs/event-hubs-what-is-event-hubs) et [IOT Hub](/azure/iot-hub) à [service bus](/azure/service-bus). Quel que soit le transport, sans serveur est un mécanisme idéal pour le traitement des messages et des flux de données au fur et à mesure de leur arrivée. Sans serveur peut évoluer rapidement pour répondre à la demande de grands volumes de données. Le code sans serveur peut appliquer la logique métier pour analyser les données et les sorties dans un format structuré pour l’action et l’analyse.

![Traitement de flux sans serveur](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Passerelle API

Une passerelle d’API fournit un point unique d’entrée pour les clients, puis achemine intelligemment les demandes aux services principaux. Il est utile de gérer de grands ensembles de services. Il peut également gérer le contrôle de version et simplifier le développement en connectant facilement les clients à des environnements disparates. Sans serveur peut gérer la mise à l’échelle du serveur principal des microservices individuels tout en présentant un seul serveur frontal via une passerelle d’API.

![Passerelle d’API sans serveur](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Ressources recommandées

- [Azure Event Grid](/azure/event-grid/overview)
- [Azure IoT Hub](/azure/iot-hub)
- [Problématiques et solutions pour la gestion des données distribuées](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [Conception de microservices : identification des limites de microservice](/azure/architecture/microservices/microservice-boundaries)
- [Hubs d'événements](/azure/event-hubs/event-hubs-what-is-event-hubs)
- [Modèle d’approvisionnement en événements](/azure/architecture/patterns/event-sourcing)
- [Implémentation du modèle Disjoncteur](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [IoT Hub](/azure/iot-hub)
- [Service Bus](/azure/service-bus)
- [Utilisation du support de flux de modification dans Azure Cosmos DB](/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Précédent](serverless-architecture-considerations.md) 
> [Suivant](azure-serverless-platform.md)
