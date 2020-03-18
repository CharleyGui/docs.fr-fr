---
title: Exemples de conception sans serveur - Applications sans serveur
description: Comprendre la variété des scénarios pris en charge par des architectures sans serveur, de la planification et le traitement basé sur les événements aux déclencheurs de fichiers et au processus de flux.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4e8fda0c1423c881c0807602e11f7c49ff7cfe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73093554"
---
# <a name="serverless-design-examples"></a>Exemples de conceptions serverless

Il existe de nombreux modèles de conception qui existent pour sans serveur. Cette section capture certains scénarios courants qui utilisent sans serveur. Ce que tous les exemples ont en commun, c’est la combinaison fondamentale d’un déclencheur d’événements et de la logique commerciale.

## <a name="scheduling"></a>Planification

La planification des tâches est une fonction courante. Le diagramme suivant montre une base de données héritée qui ne fait pas l’œster approprié. La base de données doit être nettoyée périodiquement. La fonction sans serveur trouve des données non valides et les nettoie. Le déclencheur est une minuterie qui exécute le code sur un calendrier.

![Planification sans serveur](./media/serverless-scheduling.png)

## <a name="command-and-query-responsibility-segregation-cqrs"></a>Séparation des responsabilités en matière de commande et de requête (CQRS)

La ségrégation des responsabilités de commandement et de requête (CQRS) est un modèle qui fournit différentes interfaces pour lire (ou interroger) les données et les opérations qui modifient les données. Il aborde plusieurs problèmes courants. Dans les systèmes traditionnels basés sur la suppression de la mise à jour Create Read Delete (CRUD), les conflits peuvent provenir d’un volume élevé de lectures et d’écrits dans le même magasin de données. Le verrouillage peut souvent se produire et ralentir considérablement les lectures. Souvent, les données sont présentées comme un composite de plusieurs objets de domaine et les opérations de lecture doivent combiner les données de différentes entités.

À l’aide de CQRS, une lecture peut impliquer une entité spéciale « aplatie » qui modélise les données de la façon dont elle est consommée. La lecture est traitée différemment de la façon dont il est stocké. Par exemple, bien que la base de données puisse stocker un contact comme enregistrement d’en-tête avec un enregistrement d’adresse d’enfant, la lecture peut impliquer une entité avec des propriétés d’en-tête et d’adresse. Il existe une myriade d’approches pour créer le modèle de lecture. Il pourrait être matérialisé à partir des points de vue. Les opérations de mise à jour pourraient être encapsulées comme des événements isolés qui déclenchent ensuite des mises à jour de deux modèles différents. Des modèles distincts existent pour la lecture et l’écriture.

![Exemple de CQRS](./media/cqrs-example.png)

Serverless peut s’adapter au modèle CQRS en fournissant les points de terminaison séparés. Une fonction sans serveur s’adapte aux requêtes ou aux lectures, et une fonction ou un ensemble de fonctions différents sans serveur gère les opérations de mise à jour. Une fonction sans serveur peut également être responsable de maintenir le modèle de lecture à jour, et peut être déclenchée par le flux de [changement](https://docs.microsoft.com/azure/cosmos-db/change-feed)de la base de données . Le développement frontale est simplifié pour se connecter aux critères d’évaluation nécessaires. Le traitement des événements est géré à l’arrière. Ce modèle s’évolue également bien pour les grands projets car différentes équipes peuvent travailler sur différentes opérations.

## <a name="event-based-processing"></a>Traitement événementiel

Dans les systèmes basés sur les messages, les événements sont souvent rassemblés dans les files d’attente ou les sujets de l’éditeur/abonné à prendre en compte. Ces événements peuvent déclencher des fonctions sans serveur pour exécuter un morceau de logique d’entreprise. Un exemple de traitement basé sur les événements est les systèmes d’origine événementiel. Un « événement » est soulevé pour marquer une tâche aussi complète. Une fonction sans serveur déclenchée par l’événement met à jour le document de base de données approprié. Une deuxième fonction sans serveur peut utiliser l’événement pour mettre à jour le modèle de lecture pour le système. [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) offre un moyen d’intégrer les événements avec les fonctions en tant qu’abonnés.

> Les événements sont des messages d’information. Pour plus d’informations, voir [Le modèle d’approvisionnement d’événements](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

## <a name="file-triggers-and-transformations"></a>Déclencheurs et transformations de fichiers

Extrait, Transform, and Load (ETL) est une fonction commerciale commune. Serverless est une excellente solution pour ETL car il permet de déclencher du code dans le cadre d’un pipeline. Les composants de code individuels peuvent aborder divers aspects. Une fonction sans serveur peut télécharger le fichier, une autre applique la transformation, et une autre charge les données. Le code peut être testé et déployé indépendamment, ce qui facilite l’entretien et l’échelle au besoin.

![Déclencheurs et transformations de fichiers sans serveur](./media/serverless-file-triggers.png)

Dans le diagramme, "cool storage" fournit des données qui sont analysées dans [Azure Stream Analytics](https://docs.microsoft.com/azure/stream-analytics). Tous les problèmes rencontrés dans le flux de données déclenchent une fonction Azure pour remédier à l’anomalie.

## <a name="asynchronous-background-processing-and-messaging"></a>Traitement et messagerie de fond asynchrones

La messagerie asynchrone et le traitement de fond permettent aux applications de lancer des processus sans avoir à attendre. Un exemple de traitement asynchrone est une application OCR. Une image est soumise et mise en file d’attente pour le traitement. La numérisation de l’image pour extraire du texte peut prendre du temps, et une fois qu’il est terminé une notification est envoyée. Serverless peut gérer à la fois l’invocation et le résultat dans ce scénario.

## <a name="web-apps-and-apis"></a>API et applications web

Un scénario populaire pour sans serveur est les applications de niveau N, le plus souvent ceux où la couche d’interface utilisateur est une application web. La popularité des applications à page unique (SPA) a récemment bondi. Les applications SPA rendent une seule page, puis s’appuient sur les appels API et les données retournées pour rendre dynamiquement la nouvelle interface utilisateur sans recharger une pleine page. Le rendu côté client fournit une application beaucoup plus rapide et plus réactive à l’utilisateur final.

Les paramètres sans serveur déclenchés par les appels HTTP peuvent être utilisés pour traiter les demandes d’API. Par exemple, une société de services publicitaires peut appeler une fonction sans serveur avec des informations de profil utilisateur pour demander de la publicité personnalisée. La fonction sans serveur renvoie l’annonce personnalisée et la page Web la rend.

![API Web sans serveur](./media/serverless-web-api.png)

## <a name="data-pipeline"></a>Pipeline de données

Les fonctions sans serveur peuvent être utilisées pour faciliter un pipeline de données. Dans cet exemple, un fichier déclenche une fonction pour traduire des données dans un fichier CSV en lignes de données dans un tableau. Le tableau organisé permet à un tableau de bord Power BI de présenter l’analyse à l’utilisateur final.

![Pipeline de données sans serveur](./media/serverless-data-pipeline.png)

## <a name="stream-processing"></a>Traitement des flux de données

Les appareils et les capteurs génèrent souvent des flux de données qui doivent être traitées en temps réel. Il existe un certain nombre de technologies qui peuvent capturer des messages et des flux à partir de [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs) et [IoT Hub](https://docs.microsoft.com/azure/iot-hub) à [Service Bus](https://docs.microsoft.com/azure/service-bus). Quel que soit le transport, sans serveur est un mécanisme idéal pour traiter les messages et les flux de données au fur et à mesure qu’ils entrent en jeu. Serverless peut évoluer rapidement pour répondre à la demande de grands volumes de données. Le code sans serveur peut appliquer la logique d’entreprise pour analyser les données et la sortie dans un format structuré pour l’action et l’analyse.

![Traitement de flux sans serveur](./media/serverless-stream-processing.png)

## <a name="api-gateway"></a>Passerelle API

Une passerelle API offre un point d’entrée unique pour les clients, puis achemine intelligemment les demandes de services back-end. Il est utile de gérer de grands ensembles de services. Il peut également gérer la version et simplifier le développement en connectant facilement les clients à des environnements disparates. Serverless peut gérer la mise à l’échelle back-end des microservices individuels tout en présentant une seule extrémité avant via une passerelle API.

![Passerelle API sans serveur](./media/serverless-api-gateway.png)

## <a name="recommended-resources"></a>Ressources recommandées

- [Grille d’événements Azure](https://docs.microsoft.com/azure/event-grid/overview)
- [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Défis et solutions pour la gestion des données distribuée](../microservices/architect-microservice-container-applications/distributed-data-management.md)
- [Conception de microservices : identification des limites des microservices](https://docs.microsoft.com/azure/architecture/microservices/microservice-boundaries)
- [Event Hubs](https://docs.microsoft.com/azure/event-hubs/event-hubs-what-is-event-hubs)
- [Modèle d'approvisionnement en événements](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)
- [Implémentation du modèle Disjoncteur](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md)
- [IoT Hub](https://docs.microsoft.com/azure/iot-hub)
- [Service Bus](https://docs.microsoft.com/azure/service-bus)
- [Utilisation du support de flux de modification dans Azure Cosmos DB](https://docs.microsoft.com/azure/cosmos-db/change-feed)

>[!div class="step-by-step"]
>[Suivant précédent](serverless-architecture-considerations.md)
>[Next](azure-serverless-platform.md)
