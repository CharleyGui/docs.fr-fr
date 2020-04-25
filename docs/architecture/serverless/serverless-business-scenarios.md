---
title: Exemples de scénarios d’entreprise et de cas d’utilisation pour les applications sans serveur
description: Découvrez sans serveur une approche pratique en accédant à des exemples qui vont du traitement de l’image à la prise en charge mobile et aux pipelines ETL.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 3cb3b73325fccc327ccf17f7298048f2eeb3577a
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158448"
---
# <a name="serverless-business-scenarios-and-use-cases"></a>Scénarios métier et cas d’usage serverless

Il existe de nombreux scénarios et scénarios d’utilisation pour les applications sans serveur. Ce chapitre contient des exemples qui illustrent les différents scénarios. Les scénarios incluent des liens vers la documentation connexe et les référentiels de code source publics. Les exemples de ce chapitre vous permettent de commencer à créer et à mettre en œuvre des solutions sans serveur.

## <a name="big-data-processing"></a>Traitement du Big Data

![Diagramme de mappage/réduction](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

Cet exemple utilise sans serveur pour effectuer une opération de mappage/réduction sur un jeu de Big Data. Il détermine la vitesse moyenne des voyages de taxis jaunes de New York par jour en 2017.

[Traitement des données Big Data : MapReduce sans serveur sur Azure](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a>Créer des applications sans serveur : laboratoire pratique

Découvrez comment utiliser les fonctions pour exécuter une logique côté serveur et créer des architectures sans serveur.

- Choix du meilleur service Azure pour votre entreprise
- Création d’Azure Functions
- Utilisation de déclencheurs
- Chaînage des fonctions
- Flux de travail de longue durée
- Surveillance
- Développement, test et déploiement

[Créer des applications sans serveur](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a>Révisions client

Cet exemple illustre les nouveaux outils de Azure Functions pour les bibliothèques de classes C# dans Visual Studio. Créez un site Web où les clients envoient des avis de produits stockés dans les objets BLOB de stockage Azure et CosmosDB. Ajoutez une fonction Azure pour effectuer une modération automatique des évaluations des clients à l’aide d’Azure Cognitive Services. Utilisez une file d’attente de stockage Azure pour découpler le site Web de la fonction.

[Application de révisions du client avec Cognitive Services](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a>Prise en charge des images Linux de l’arrimeur

Cet exemple montre comment créer un `Dockerfile` pour générer et exécuter des Azure Functions sur un conteneur d’ancrage Linux.

[Azure Functions sur Linux](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a>Traitement et validation des fichiers

Cet exemple analyse un ensemble de fichiers CSV provenant de clients hypothétiques. Il garantit que tous les fichiers requis pour un client « batch » sont prêts, puis valide la structure de chaque fichier. Différentes solutions sont présentées à l’aide de Azure Functions, Logic Apps et Durable Functions.

[Traitement des fichiers et validation à l’aide de Azure Functions, Logic Apps et Durable Functions](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a>Visualisation des données du jeu

![Télémétrie de jeu](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

Exemple de la façon dont un développeur peut implémenter une solution de visualisation des données dans l’éditeur pour son jeu. En fait, un plug-in de moteur 4 non réel et un plug-in Unity ont été développés à l’aide de cet exemple comme backend. Le composant de service est indépendant du moteur de jeu.

[Visualisation de la télémétrie du jeu dans l’éditeur](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a>GraphQL

Créer une fonction sans serveur qui expose une API GraphQL.

[Fonctions sans serveur pour GraphQL](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a>Relais de périphérie Reliable Internet des objets (IoT)

![Architecture IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

Cet exemple implémente un nouveau protocole de communication pour activer la communication en amont fiable à partir des appareils IoT. Il automatise la détection et le renvoi des écarts de données.

[Relais de périphérie Reliable IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a>Architecture de référence des microservices

![Architecture de référence](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

Architecture de référence qui vous guide tout au long du processus de prise de décision impliqué dans la conception, le développement et la diffusion de l’application RideShare by Relecloud (une société fictive). Il comprend des instructions pratiques pour la configuration et le déploiement de tous les composants de l’architecture.

[Architecture de référence des microservices sans serveur](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a>Migrer des applications console vers sans serveur

Cet exemple est une fonction générique (`.csx` fichier) qui peut être utilisée pour convertir n’importe quelle application console en service Web HTTP dans Azure functions. Il vous suffit de modifier un fichier de configuration et de spécifier les paramètres d’entrée qui seront passés comme arguments à `.exe`l'.

[Exécuter des applications de console sur Azure Functions](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a>Sans serveur pour les appareils mobiles

Les Azure Functions sont faciles à implémenter et à gérer, et accessibles via HTTP. Ils constituent un excellent moyen d’implémenter une API pour une application mobile. Microsoft propose de superbes outils multiplateformes pour iOS, Android et Windows avec Xamarin. En tant que tel, Xamarin et Azure Functions fonctionnent bien ensemble. Cet article explique comment implémenter une fonction Azure dans le Portail Azure ou dans Visual Studio au début, et comment créer un client multiplateforme avec Xamarin. Forms s’exécutant sur Android, iOS et Windows.

[Implémentation d’une fonction Azure simple avec un client Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a>Messagerie sans serveur

Cet exemple montre comment utiliser le modèle de Fanout Durable Functions pour charger un nombre arbitraire de messages sur un nombre quelconque de sessions/partitions. Il cible les files d’attente Service Bus, Event Hubs ou de stockage. L’exemple ajoute également la possibilité d’utiliser ces messages avec une autre fonction Azure et de charger les données de minutage qui en résultent dans un autre concentrateur d’événements. Les données sont ensuite ingérées dans Analytics services comme Azure Explorateur de données.

[Générez et consommez des messages via les files d’attente Service Bus, Event Hubs et de stockage avec Azure Functions](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a>Ressources recommandées

- [Azure Functions sur Linux](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [Traitement des données Big Data : MapReduce sans serveur sur Azure](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [Créer des applications sans serveur](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [Application de révisions du client avec Cognitive Services](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [Traitement des fichiers et validation à l’aide de Azure Functions, Logic Apps et Durable Functions](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [Implémentation d’une fonction Azure simple avec un client Xamarin. Forms](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [Visualisation de la télémétrie du jeu dans l’éditeur](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [Relais de périphérie Reliable IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [Générez et consommez des messages via les files d’attente Service Bus, Event Hubs et de stockage avec Azure Functions](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [Exécuter des applications de console sur Azure Functions](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [Fonctions sans serveur pour GraphQL](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [Architecture de référence des microservices sans serveur](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
>[Précédent](orchestration-patterns.md)
>[suivant](serverless-conclusion.md)
