---
title: Résumé
description: Résumé des principales conclusions tirées de la présentation de l’architecture des applications .NET natives du Cloud pour Azure Guide/e-book.
ms.date: 04/29/2020
ms.openlocfilehash: 8cad8df1f69e159caf88d3ee119278dff8726385
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395319"
---
# <a name="summary"></a>Résumé

En résumé, Voici les conclusions importantes de ce guide :

- **Cloud-Native** consiste à concevoir des applications modernes qui prennent en charge un changement rapide, une grande échelle et une résilience, dans des environnements dynamiques modernes, tels que des clouds publics, privés et hybrides.

- **CNCF ( [Cloud Native Computing Foundation](https://www.cncf.io/) )** est un consortium open source influent de plus de 300 entreprises majeures. Il est responsable de la conduite de l’adoption de l’informatique Native Cloud sur la technologie et les piles du Cloud.

- **Les instructions CNCF** recommandent que les applications Cloud natives adoptent six piliers importants, comme illustré dans la figure 11-1 :

  ![Piliers natifs du Cloud](./media/cloud-native-foundational-pillars.png)

  **Figure 11-1** : Piliers natifs du Cloud

- Ces piliers natifs du Cloud sont les suivants :
  - Le Cloud et son modèle de service sous-jacent
  - Principes de conception modernes
  - Microservices
  - Conteneur et orchestration de conteneur
  - Services de stockage basés sur le Cloud, tels que les bases de données et les courtiers de messages
  - Automatisation, y compris l’infrastructure en tant que code et déploiement de code

- **Kubernetes** est l’environnement d’hébergement de Choice pour la plupart des applications Cloud natives. Des services plus petits et simples sont parfois hébergés sur des plateformes sans serveur, telles que Azure Functions. Parmi les nombreuses fonctionnalités d’automatisation clés, les deux environnements offrent une mise à l’échelle automatique pour gérer les volumes fluctuants de charge de travail.

- La communication avec le **service** devient une décision de conception significative lors de la construction d’une application Cloud native. Les applications exposent généralement une passerelle d’API pour gérer les communications des clients frontaux. Ensuite, les microservices principaux s’efforcent de communiquer entre eux en implémentant des modèles de communication asynchrone, lorsque cela est possible.

- **gRPC** est une infrastructure moderne et hautement performante qui fait évoluer le protocole d’appel de procédure distante (RPC) Age Old. Les applications Cloud natives adoptent souvent gRPC pour simplifier la messagerie entre les services principaux. gRPC utilise HTTP/2 pour son protocole de transport. Elle peut être jusqu’à 8 fois plus rapide que la sérialisation JSON avec des tailles de message de 60-80% plus petite. gRPC est open source et géré par la CNCF (Cloud Native Computing Foundation).

- Les **données distribuées** sont souvent implémentées par des applications Cloud natives. Les applications séparent les fonctionnalités d’entreprise en microservices indépendants et de petite taille. Chaque microservice encapsule ses propres dépendances, données et état. Le modèle de base de données partagée classique évolue dans l’une des nombreuses bases de données les plus petites, chacune s’alignant sur un microservice. Lorsque la fumée disparaît, nous avons découvert une conception qui expose un `database-per-microservice` modèle.

- **Les bases de données non-SQL** font référence aux banques de données hautes performances et non relationnelles. Ils utilisent Excel dans leurs caractéristiques de facilité d’utilisation, d’évolutivité, de résilience et de disponibilité. Les services de volume élevés qui nécessitent un temps de réponse inférieur à la seconde favorisent les banques de données NoSQL. La prolifération des technologies NoSQL pour les systèmes Cloud natifs distribués ne peut pas être surétate.

- **NewSQL** est une technologie de base de données émergente qui combine l’évolutivité distribuée de NoSQL et les garanties acid d’une base de données relationnelle. Les bases de données NewSQL ciblent des systèmes d’entreprise qui doivent traiter de gros volumes de données, dans des environnements distribués, avec une conformité transactionnelle/ACID complète. CNCF (Cloud Native Computing Foundation) propose plusieurs projets de base de données NewSQL.

- La **résilience** est la capacité de votre système à réagir à une défaillance tout en restant fonctionnelle. Les systèmes Cloud natifs intègrent l’architecture distribuée dans laquelle l’échec est inévitable. Les applications doivent être construites pour répondre de manière élégante aux défaillances et revenir rapidement à un état de fonctionnement complet.

- Les **maillages de service** sont une couche d’infrastructure configurable avec des fonctionnalités intégrées permettant de gérer la communication entre les services et d’autres défis transversaux. Ils découplent les responsabilités croisées de votre code d’entreprise. Ces responsabilités se déplacent dans un proxy de service. Appelé `Sidecar pattern` , le proxy est déployé dans un processus distinct pour assurer l’isolation à partir de votre code d’entreprise.

- L' **observation** est un facteur clé pour la conception des applications Cloud natives. À mesure que les services sont distribués sur un cluster de nœuds, la journalisation centralisée, la surveillance et les alertes, deviennent obligatoires. Azure Monitor est une collection d’outils basés sur le Cloud conçue pour offrir une visibilité de l’état de votre système.

- L' **infrastructure en tant que code** est une pratique largement acceptée qui automatise l’approvisionnement de la plateforme. Votre infrastructure et vos déploiements sont automatisés, cohérents et reproductibles. Des outils comme Azure Resource Manager, Terraform et Azure CLI, vous permettent de générer un script de façon déclarative de l’infrastructure cloud dont vous avez besoin.

- L' **automatisation du code** est requise pour les applications Cloud natives. Les systèmes d’intégration continue et de CD modernes aident à respecter ce principe. Ils fournissent des étapes de génération et de déploiement distinctes qui permettent de garantir un code cohérent et de qualité. L’étape de génération transforme le code en artefact binaire. L’étape de mise en service récupère l’artefact binaire, applique la configuration de l’environnement externe et le déploie dans un environnement spécifié. Azure DevOps et GitHub sont des environnements DevOps complets.

>[!div class="step-by-step"]
>[Précédent](application-bundles.md)
