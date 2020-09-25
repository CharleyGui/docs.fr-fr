---
title: Architecture sans serveur-applications sans serveur
description: Exploration des différentes architectures et applications prises en charge par les architectures sans serveur, y compris les applications Web, mobiles et IoT.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: f7d80ce3957c2ad90a67ae6ba1fc2786af30fcc1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171713"
---
# <a name="serverless-architecture"></a>Architecture serverless

Il existe de nombreuses approches pour l’utilisation d’architectures sans [serveur](https://azure.com/serverless) . Ce chapitre explore des exemples d’architectures courantes qui intègrent sans serveur. Il aborde également les problèmes qui peuvent poser des problèmes supplémentaires ou nécessiter une attention particulière lors de l’implémentation sans serveur. Enfin, plusieurs exemples de conception sont fournis, qui illustrent différents cas d’utilisation sans serveur.

Les hôtes sans serveur utilisent souvent une couche de conteneur ou PaaS existante pour gérer les instances sans serveur. Par exemple, Azure Functions est basé sur [Azure App service](/azure/app-service/). Le App Service est utilisé pour monter en charge les instances et gérer le runtime qui exécute Azure Functions code. Pour les fonctions basées sur Windows, l’hôte s’exécute en tant que PaaS et met à l’échelle le Runtime .NET. Pour les fonctions basées sur Linux, l’hôte utilise des conteneurs.

![Architecture Azure Functions](./media/azure-functions-architecture.png)

Le noyau des tâches Web fournit un contexte d’exécution pour la fonction. Le runtime du langage exécute des scripts, exécute des bibliothèques et héberge l’infrastructure pour le langage cible. Par exemple, Node.js est utilisé pour exécuter des fonctions JavaScript et le .NET Framework est utilisé pour exécuter des fonctions C#. Vous en apprendrez davantage sur les options de langue et de plateforme plus loin dans ce chapitre.

Certains projets peuvent tirer parti d’une approche « tout-en-un » pour les serveurs sans serveur. Les applications qui s’appuient fortement sur les microservices peuvent implémenter tous les microservices à l’aide d’une technologie sans serveur. La majorité des applications sont hybrides, à la suite d’une conception à N niveaux et en utilisant sans serveur les composants qui sont logiques, car les composants sont modulaires et à l’échelle indépendante. Pour vous aider à comprendre ces scénarios, cette section décrit quelques exemples d’architecture courants qui utilisent sans serveur.

## <a name="full-serverless-back-end"></a>back end sans serveur complète

La back end complète sans serveur est idéale pour plusieurs types de scénarios, en particulier lors de la création d’applications de « champ vert ». Une application avec une grande surface d’API peut tirer parti de l’implémentation de chaque API comme une fonction sans serveur. Les applications basées sur l’architecture de microservices sont un autre exemple qui peut être implémenté en tant que back end sans serveur complète. Les microservices communiquent par l’intermédiaire de différents protocoles. Voici quelques scénarios spécifiques :

- Produits SaaS basés sur une API (exemple : le processeur de paiements financiers).
- Applications pilotées par les messages (exemple : solution de surveillance des appareils).
- Applications axées sur l’intégration entre les services (exemple : application de réservation d’une compagnie aérienne).
- Processus qui s’exécutent périodiquement (par exemple, nettoyage de base de données basé sur un minuteur).
- Applications axées sur la transformation des données (exemple : importation déclenchée par le chargement de fichiers).
- Extrayez les processus de transformation et de chargement (ETL).

D’autres cas d’utilisation plus spécifiques sont couverts plus loin dans ce document.

## <a name="monoliths-and-starving-the-beast"></a>Monolithiques et « prive the animaux »

La migration d’une application monolithique existante vers le Cloud constitue un défi courant. L’approche la moins risquée consiste à « élever et déplacer » entièrement sur des machines virtuelles. De nombreux magasins préfèrent utiliser la migration comme une opportunité de moderniser leur base de code. La migration est une approche pratique de la migration. Dans ce scénario, le monolithe est migré « en l’environnement » pour commencer par. Les services sélectionnés sont ensuite modernisés. Dans certains cas, la signature du service est identique à l’original : elle est simplement hébergée en tant que fonction. Les clients sont mis à jour pour utiliser le nouveau service plutôt que le point de terminaison monolithe. Dans l’intervalle, des étapes telles que la réplication de base de données permettent aux microservices d’héberger leur propre stockage même lorsque les transactions sont toujours gérées par le monolithique. Finalement, tous les clients sont migrés vers les nouveaux services. Le monolithe est « privé » (ses services ne sont plus appelés) tant que toutes les fonctionnalités n’ont pas été remplacées. La combinaison de serveurs et de proxys peut faciliter la majeure partie de cette migration.

![Migration de monolithique sans serveur](./media/serverless-monolith-migration.png)

Pour en savoir plus sur cette approche, regardez la vidéo : [Placez votre application dans le Cloud avec des Azure Functions sans serveur](https://channel9.msdn.com/Events/Connect/2017/E102).

## <a name="web-apps"></a>les applications web

Les applications Web sont de bons candidats pour les applications sans serveur. Il existe aujourd’hui deux approches courantes des applications Web : pilotées par le serveur et pilotées par le client (par exemple, une application à page unique ou SPA). Les applications Web pilotées par serveur utilisent généralement une couche intergiciel (middleware) pour émettre des appels d’API afin de rendre l’interface utilisateur Web. Les applications SPA effectuent des appels d’API REST directement à partir du navigateur. Dans les deux scénarios, sans serveur peut prendre en charge la demande d’API REST ou middleware en fournissant la logique métier nécessaire. Une architecture courante consiste à créer un serveur Web statique léger. L’application à page unique (SPA) sert les ressources HTML, CSS, JavaScript et d’autres navigateurs. L’application Web se connecte ensuite à un back end de microservices.

## <a name="mobile-back-ends"></a>Back-end mobile

Le paradigme piloté par les événements des applications sans serveur les rend idéales en back-end mobile. Le périphérique mobile déclenche les événements et le code sans serveur s’exécute pour répondre aux demandes. Tirer parti d’un modèle sans serveur permet aux développeurs d’améliorer la logique métier sans avoir à déployer une mise à jour complète de l’application. L’approche sans serveur permet également aux équipes de partager des points de terminaison et de travailler en parallèle.

Les développeurs mobiles peuvent créer une logique métier sans devenir des experts côté serveur. Traditionnellement, les applications mobiles sont connectées à des services locaux. Création de la couche de service nécessaire pour comprendre la plate-forme serveur et le paradigme de programmation. Les développeurs ont travaillé avec des opérations pour approvisionner les serveurs et les configurer de manière appropriée. Parfois, des jours voire des semaines ont été consacrés à la création d’un pipeline de déploiement. Tous ces problèmes sont résolus sans serveur.

Sans serveur fait abstraction des dépendances côté serveur et permet au développeur de se concentrer sur la logique métier. Par exemple, un développeur mobile qui crée des applications à l’aide d’une infrastructure JavaScript peut également créer des fonctions sans serveur avec JavaScript. L’hôte sans serveur gère le système d’exploitation, une instance de Node.js pour héberger le code, les dépendances de package, etc. Le développeur a fourni un ensemble simple d’entrées et un modèle standard pour les sorties. Ils peuvent ensuite se concentrer sur la création et le test de la logique métier. Ils sont donc en mesure d’utiliser les compétences existantes pour créer la logique principale de l’application mobile sans avoir à apprendre de nouvelles plateformes ou devenir un « développeur côté serveur ».

![back end mobile sans serveur](./media/serverless-mobile-backend.png)

La plupart des fournisseurs de Cloud offrent des produits sans serveur mobiles qui simplifient l’ensemble du cycle de vie de développement mobile. Les produits peuvent automatiser le provisionnement des bases de données pour conserver les données, gérer les préoccupations des DevOps, fournir des builds basées sur le Cloud et des infrastructures de test, ainsi que la possibilité de créer des scripts pour les processus d’entreprise à l’aide du langage préféré du développeur. Suivre une approche sans serveur axée sur mobile peut simplifier le processus. Sans serveur supprime l’énorme traitement de l’approvisionnement, de la configuration et de la maintenance des serveurs pour les back end mobiles.

## <a name="internet-of-things-iot"></a>Internet des objets (IoT)

IoT fait référence aux objets physiques qui sont reliés en réseau. Ils sont parfois appelés « appareils connectés » ou « Smart Devices ». Tout ce qui se trouve dans les voitures et les distributeurs peut être connecté et envoyer des informations allant de l’inventaire aux données de capteur, telles que la température et l’humidité. Dans l’entreprise, IoT fournit des améliorations des processus d’entreprise grâce à la surveillance et à l’automatisation. Les données IoT peuvent être utilisées pour réguler le climat dans un entrepôt de grande taille ou suivre le stock dans la chaîne d’approvisionnement. IoT peut détecter les dépassements de produits chimiques et appeler le service incendie en cas de détection de fumée.

Le volume considérable d’appareils et d’informations dicte souvent une architecture pilotée par les événements pour acheminer et traiter les messages. Sans serveur est une solution idéale pour plusieurs raisons :

- Active la mise à l’échelle à mesure que le volume d’appareils et de données augmente.
- S’adapte à l’ajout de nouveaux points de terminaison pour prendre en charge de nouveaux appareils et capteurs.
- Facilite le contrôle de version indépendant afin que les développeurs puissent mettre à jour la logique métier pour un appareil spécifique sans avoir à déployer l’ensemble du système.
- Résilience et moins de temps d’arrêt.

L’omniprésence de l’IoT a donné lieu à plusieurs produits sans serveur qui se concentrent spécifiquement sur les préoccupations IoT, comme [Azure IOT Hub](/azure/iot-hub). L’automatisation sans serveur automatise des tâches telles que l’inscription des appareils, l’application des stratégies, le suivi et même le déploiement de code sur les appareils à *la périphérie*. Le périmètre fait référence à des appareils tels que les capteurs et les actionneurs qui sont connectés à Internet, mais qui ne sont pas une partie active de ce dernier.

>[!div class="step-by-step"]
>[Précédent](architecture-approaches.md) 
> [Suivant](serverless-architecture-considerations.md)
