---
title: Approches de l’architecture-applications sans serveur
description: Présentation des approches d’architecture permettant de créer des applications d’entreprise basées sur le Cloud, des architectures multicouches à des serveurs sans serveur.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 0ab84d1f3425c1fda787756b73fd8315fe6d4231
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171973"
---
# <a name="architecture-approaches"></a>Approches de l’architecture

La compréhension des approches existantes de l’architecture des applications d’entreprise permet de clarifier le rôle joué par un sans serveur. Il existe de nombreuses approches et modèles qui ont évolué au fil des décennies du développement de logiciels, et ont tous leurs propres avantages et inconvénients. Dans de nombreux cas, la solution ultime peut ne pas impliquer une seule approche, mais peut intégrer plusieurs approches. Les scénarios de migration impliquent souvent un passage d’une approche d’architecture à une autre via une approche hybride.

Ce chapitre fournit une vue d’ensemble des modèles d’architecture logique et physique pour les applications d’entreprise.

## <a name="architecture-patterns"></a>Modèles d’architecture

Les applications métier modernes suivent un large éventail de modèles d’architecture. Cette section représente une étude des modèles courants. Les modèles répertoriés ici ne sont pas nécessairement les meilleures pratiques, mais illustrent des approches différentes.

Pour plus d’informations, consultez Guide de l' [architecture des applications Azure](/azure/architecture/guide/).

## <a name="monoliths"></a>Monolithes

De nombreuses applications professionnelles suivent un modèle monolithique. Les applications héritées sont souvent implémentées en tant que monolithiques. Dans le modèle monolithique, tous les problèmes d’application sont contenus dans un seul déploiement. Tout, de l’interface utilisateur aux appels de base de données, est inclus dans la même base de code.

![Architecture monolithique](./media/monolith-architecture.png)

L’approche monolithique présente plusieurs avantages. Il est souvent facile d’extraire une base de code unique et de commencer à travailler. Le temps d’exécution de la rampe peut être inférieur, et la création d’environnements de test est aussi simple que la création d’une nouvelle copie. Le monolithe peut être conçu pour inclure plusieurs composants et applications.

Malheureusement, le modèle monolithique a tendance à s’arrêter à l’échelle. Les inconvénients majeurs de l’approche monolithique sont les suivants :

- Il est difficile de travailler en parallèle dans la même base de code.
- Toute modification, quel que soit son degré de simplicité, requiert le déploiement d’une nouvelle version de l’application entière.
- La refactorisation peut avoir un impact sur l’ensemble de l’application.
- Souvent, la seule solution à mettre à l’échelle consiste à créer plusieurs copies gourmandes en ressources du monolithique.
- À mesure que les systèmes sont développés ou que d’autres systèmes sont acquis, l’intégration peut être difficile.
- Il peut être difficile de tester en raison de la nécessité de configurer l’ensemble du monolithique.
- La réutilisation du code est délicate et souvent d’autres applications finissent par avoir leurs propres copies du code.

De nombreuses entreprises considèrent le cloud comme une opportunité de migrer des applications monolithiques et de les Refactoriser à des modèles plus utilisables. Il est courant de décomposer les applications et les composants individuels pour leur permettre d’être gérés, déployés et mis à l’échelle séparément.

## <a name="n-layer-applications"></a>Applications multicouches

Logique d’application de partition d’application à N couches dans des couches spécifiques. Les couches les plus courantes sont les suivantes :

- Interface utilisateur
- Logique métier
- Accès aux données

D’autres couches peuvent inclure des intergiciels (middleware), le traitement par lots et l’API. Il est important de noter que les couches sont logiques. Bien qu’elles soient développées de manière isolée, elles peuvent toutes être déployées sur la même plateforme cible.

![Architecture à N couches](./media/n-layer-architecture.png)

L’approche multicouche présente plusieurs avantages, notamment :

- La refactorisation est isolée dans une couche.
- Les équipes peuvent créer, tester, déployer et gérer indépendamment des couches distinctes.
- Les couches peuvent être échangées, par exemple la couche de données peut accéder à plusieurs bases de données sans nécessiter de modifications de la couche d’interface utilisateur.

Sans serveur peut être utilisé pour implémenter une ou plusieurs couches.

## <a name="microservices"></a>Microservices

Les architectures de **[microservices](/azure/architecture/guide/architecture-styles/microservices)** contiennent des caractéristiques communes qui incluent :

- Les applications sont composées de plusieurs petits services.
- Chaque service s’exécute dans son propre processus.
- Les services sont alignés autour des domaines d’entreprise.
- Les services communiquent via des API légères, en utilisant généralement HTTP comme transport.
- Les services peuvent être déployés et mis à niveau indépendamment.
- Les services ne sont pas dépendants d’un seul magasin de données.
- Le système est conçu en cas d’échec, et l’application peut toujours s’exécuter même lorsque certains services échouent.

Il n’est pas nécessaire que les microservices soient mutuellement exclusifs à d’autres approches d’architecture. Par exemple, une architecture multiniveau peut utiliser des microservices pour la couche intermédiaire. Il est également possible d’implémenter des microservices de différentes façons, des répertoires virtuels sur les hôtes IIS aux conteneurs. Les caractéristiques des microservices les rendent particulièrement idéales pour les implémentations sans serveur.

![Architecture de microservices](./media/microservices-architecture.png)

Les avantages des architectures de microservices sont les suivants :

- La refactorisation est souvent isolée dans un service unique.
- Les services peuvent être mis à niveau indépendamment l’un de l’autre.
- La résilience et l’élasticité peuvent être réglées sur les demandes des services individuels.
- Le développement peut se faire en parallèle sur des plateformes et des équipes disparates.
- Il est plus facile d’écrire des tests complets pour les services isolés.

Les microservices sont accompagnés de leurs propres défis, notamment :

- Déterminer quels services sont disponibles et comment les appeler.
- Gestion du cycle de vie des services.
- Comprendre comment les services s’intègrent à l’ensemble de l’application.
- Test complet du système des appels effectués sur des services disparates.

En fin de compte, il existe des solutions pour répondre à tous ces défis, y compris pour tirer parti des avantages des services sans serveur décrits plus loin.

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](architecture-deployment-approaches.md)
