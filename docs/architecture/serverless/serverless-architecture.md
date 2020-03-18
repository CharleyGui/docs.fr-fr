---
title: Architecture sans serveur - Applications sans serveur
description: Exploration de diverses architectures et applications qui sont prises en charge par des architectures sans serveur, y compris les applications Web, mobiles et IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 838dcd7b41df0d8297e1ae10f9c04a8d5b83b332
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522406"
---
# <a name="serverless-architecture"></a>Architecture serverless

Il existe de nombreuses approches pour utiliser des architectures [sans serveur.](https://azure.com/serverless) Ce chapitre explore des exemples d’architectures communes qui intègrent sans serveur. Il couvre également les préoccupations qui peuvent poser des défis supplémentaires ou nécessitent une considération supplémentaire lors de la mise en œuvre sans serveur. Enfin, plusieurs exemples de conception sont fournis qui illustrent divers cas d’utilisation sans serveur.

Les hôtes sans serveur utilisent souvent une couche existante basée sur un conteneur ou PaaS pour gérer les instances sans serveur. Par exemple, Azure Functions est basé sur [Azure App Service](https://docs.microsoft.com/azure/app-service/). Le service d’application est utilisé pour dét évoluer les instances et gérer le temps d’exécution qui exécute le code Azure Functions. Pour les fonctions basées sur Windows, l’hôte fonctionne comme PaaS et à l’échelle du temps d’exécution .NET. Pour les fonctions basées sur Linux, l’hôte tire parti des conteneurs.

![Architecture Azure Functions](./media/azure-functions-architecture.png)

Le WebJobs Core fournit un contexte d’exécution pour la fonction. Le Language Runtime exécute des scripts, exécute des bibliothèques et héberge le cadre de la langue cible. Par exemple, Node.js est utilisé pour exécuter des fonctions JavaScript et le cadre .NET est utilisé pour exécuter les fonctions C. Vous en apprendrez davantage sur les options linguistiques et de plateformes plus tard dans ce chapitre.

Certains projets peuvent bénéficier d’une approche « all-in » à l’inseulante à l’arrêt serverless. Les applications qui dépendent fortement des microservices peuvent implémenter tous les microservices à l’aide de la technologie sans serveur. La majorité des applications sont hybrides, suivant une conception de niveau N et en utilisant sans serveur pour les composants qui ont du sens parce que les composants sont modulaires et indépendamment évolutifs. Pour donner un sens à ces scénarios, cette section parcourt quelques exemples d’architecture communs qui utilisent sans serveur.

## <a name="full-serverless-back-end"></a>Fin arrière sans serveur complet

L’arrière sans serveur complet est idéal pour plusieurs types de scénarios, en particulier lors de la construction de nouvelles applications ou de «champ vert». Une application avec une grande surface d’API peut bénéficier de la mise en œuvre de chaque API en tant que fonction sans serveur. Les applications qui sont basées sur l’architecture des microservices sont un autre exemple qui pourrait être mis en œuvre comme un back end sans serveur complet. Les microservices communiquent entre eux sur différents protocoles. Les scénarios spécifiques comprennent :

- Produits SaaS basés sur l’API (exemple : processeur de paiements financiers).
- Applications axées sur les messages (exemple : solution de surveillance des périphériques).
- Les applications se concentrent sur l’intégration entre les services (exemple : application de réservation de compagnies aériennes).
- Processus qui s’exécutent périodiquement (exemple : nettoyage de base de données basé sur minuterie).
- Les applications se concentrent sur la transformation des données (exemple : importation déclenchée par le téléchargement de fichiers).
- Extraire les processus Transform and Load (ETL).

Il y a d’autres cas d’utilisation plus spécifiques qui sont couverts plus tard dans ce document.

## <a name="monoliths-and-starving-the-beast"></a>Monolithes et "affamé la bête"

Un défi commun est de migrer une application monolithique existante vers le nuage. L’approche la moins risquée est de « soulever et de passer » entièrement sur des machines virtuelles. De nombreux magasins préfèrent utiliser la migration comme une occasion de moderniser leur base de code. Une approche pratique de la migration est appelée « mourir de faim de la bête ». Dans ce scénario, le monolithe est migré " tel qu’il est " pour commencer. Ensuite, certains services sont modernisés. Dans certains cas, la signature du service est identique à l’original : elle est simplement hébergée en fonction. Les clients sont mis à jour pour utiliser le nouveau service plutôt que le critère d’évaluation du monolithe. Dans l’intervalle, des étapes telles que la réplication des bases de données permettent aux microservices d’accueillir leur propre stockage même lorsque les transactions sont toujours traitées par le monolithe. Finalement, tous les clients sont migrés vers les nouveaux services. Le monolithe est " affamé " (ses services ne sont plus appelés) jusqu’à ce que toutes les fonctionnalités soient remplacées. La combinaison de serveurs et de procurations peut faciliter une grande partie de cette migration.

![Migration monolithe sans serveur](./media/serverless-monolith-migration.png)

Pour en savoir plus sur cette approche, regardez la vidéo : [Apportez votre application au cloud avec des fonctions Azure sans serveur](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>les applications web

Les applications Web sont d’excellents candidats pour des applications sans serveur. Il existe aujourd’hui deux approches courantes des applications Web : axée sur le serveur et axée sur le client (comme l’application à une page unique ou LA). Les applications Web pilotées par le serveur utilisent généralement une couche middleware pour émettre des appels API pour rendre l’interface utilisateur web. Les applications SPA effectuent des appels REST API directement à partir du navigateur. Dans les deux scénarios, sans serveur peut accueillir la demande de middleware ou REST API en fournissant la logique d’affaires nécessaire. Une architecture commune est de résister à un serveur web statique léger. L’application à une page unique (SPA) dessert HTML, CSS, JavaScript et d’autres actifs du navigateur. L’application web se connecte ensuite à un microservices back end.

## <a name="mobile-back-ends"></a>Extrémités arrière mobiles

Le paradigme event-driven des applications sans serveur les rend idéales en tant qu’extrémités arrière mobiles. L’appareil mobile déclenche les événements et le code sans serveur s’exécute pour satisfaire les demandes. Profiter d’un modèle sans serveur permet aux développeurs d’améliorer la logique métier sans avoir à déployer une mise à jour complète de l’application. L’approche sans serveur permet également aux équipes de partager des points de terminaison et de travailler en parallèle.

Les développeurs mobiles peuvent construire la logique d’entreprise sans devenir des experts du côté du serveur. Traditionnellement, les applications mobiles connectées aux services sur site. La construction de la couche de service nécessitait de comprendre la plate-forme serveur et le paradigme de programmation. Les développeurs ont travaillé avec les opérations pour fournir des serveurs et les configurer de manière appropriée. Parfois, des jours, voire des semaines, ont été consacrés à la construction d’un pipeline de déploiement. Tous ces défis sont relevés par serverless.

Serverless abstraits les dépendances côté serveur et permet au développeur de se concentrer sur la logique d’entreprise. Par exemple, un développeur mobile qui construit des applications à l’aide d’un cadre JavaScript peut également créer des fonctions sans serveur avec JavaScript. L’hôte sans serveur gère le système d’exploitation, une instance Node.js pour héberger le code, les dépendances de paquet, et plus encore. Le développeur reçoit un simple ensemble d’entrées et un modèle standard pour les sorties. Ils peuvent ensuite se concentrer sur la construction et le test de la logique d’entreprise. Ils sont donc en mesure d’utiliser les compétences existantes pour construire la logique back-end pour l’application mobile sans avoir à apprendre de nouvelles plates-formes ou devenir un "développeur côté serveur."

![Fin arrière mobile sans serveur](./media/serverless-mobile-backend.png)

La plupart des fournisseurs de cloud offrent des produits sans serveur mobiles qui simplifient l’ensemble du cycle de vie du développement mobile. Les produits peuvent automatiser la fourniture de bases de données pour persister les données, gérer les préoccupations de DevOps, fournir des builds et des cadres de test basés sur le cloud et la capacité de scripter les processus métier en utilisant la langue préférée du développeur. Suivre une approche sans serveur centrée sur le mobile peut rationaliser le processus. Serverless supprime les frais généraux énormes de provisionnement, de configuration et de maintien des serveurs pour l’arrière mobile.

## <a name="internet-of-things-iot"></a>Internet des objets (IoT)

IoT se réfère à des objets physiques qui sont mis en réseau ensemble. On les appelle parfois « appareils connectés » ou « appareils intelligents ». Tout, des voitures et des distributeurs automatiques, peut être connecté et envoyer des informations allant de l’inventaire aux données de capteurs telles que la température et l’humidité. Dans l’entreprise, IoT fournit des améliorations de processus d’affaires grâce à la surveillance et à l’automatisation. Les données de l’IoT peuvent être utilisées pour réguler le climat dans un grand entrepôt ou suivre l’inventaire à travers la chaîne d’approvisionnement. L’IoT peut détecter les déversements de produits chimiques et appeler les pompiers lorsque de la fumée est détectée.

Le volume d’appareils et d’informations dicte souvent une architecture axée sur les événements pour acheminer et traiter les messages. Serverless est une solution idéale pour plusieurs raisons :

- Permet l’échelle à mesure que le volume d’appareils et de données augmente.
- S’adapte à l’ajout de nouveaux points de terminaison pour prendre en charge de nouveaux appareils et capteurs.
- Facilite la version indépendante afin que les développeurs puissent mettre à jour la logique métier d’un appareil spécifique sans avoir à déployer l’ensemble du système.
- Résilience et moins de temps d’arrêt.

L’omniprésence de l’IoT a abouti à plusieurs produits sans serveur qui se concentrent spécifiquement sur les préoccupations IoT, tels que [Azure IoT Hub](https://docs.microsoft.com/azure/iot-hub). Serverless automatise des tâches telles que l’enregistrement des périphériques, l’application des politiques, le suivi et même le déploiement de code sur les périphériques à *la limite*. Le bord se réfère à des dispositifs comme les capteurs et les actionneurs qui sont connectés à, mais pas une partie active de l’Internet.

>[!div class="step-by-step"]
>[Suivant précédent](architecture-approaches.md)
>[Next](serverless-architecture-considerations.md)
