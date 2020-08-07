---
title: Conteneurs comme fondement de la collaboration DevOps
description: Découvrez le rôle clé des conteneurs pour rationaliser DevOps.
ms.date: 08/06/2020
ms.openlocfilehash: af28c1add8b2e6befbd2f3e6ae9fe707ccc5b106
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916021"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Conteneurs comme fondement de la collaboration DevOps

Compte tenu de la nature-même des conteneurs et de la technologie Docker, les développeurs peuvent facilement partager leurs logiciels et leurs dépendances avec le personnel informatique et des environnements de production tout en éliminant l’excuse classique « Ça fonctionne sur ma machine ». Les conteneurs résolvent les conflits d’applications entre les différents environnements. Indirectement, les conteneurs et Docker rapprochent les développeurs et le personnel informatique, en facilitant leur collaboration efficace. Adopter le workflow de conteneur offre à de nombreux clients la continuité DevOps qu’ils recherchaient mais qu’ils devaient auparavant implémenter par le biais d’une configuration plus complexe pour les pipelines de mise en production et de build. Les conteneurs simplifient les pipelines de build/test/déploiement dans DevOps.

![Diagramme montrant la propriété du cycle de vie d’une application de station d’accueil.](./media/containers-foundation-for-devops-collaboration/persona-workloads-docker-container-lifecycle.png)

**Figure 2-1.** Charges de travail principales par « personne » dans le cycle de vie des applications Docker conteneurisées

Avec les conteneurs Docker, les développeurs possèdent ce qui se trouve dans le conteneur (application, service et dépendances aux frameworks et composants) et déterminent la façon dont les conteneurs et services se comportent ensemble comme une application composée d’une collection de services. Les interdépendances des différents conteneurs sont définies dans un fichier `docker-compose.yml` ou ce qui pourrait être appelé *manifeste de déploiement*. Entre temps, les équipes informatiques (professionnels de l’informatique et gestion informatique) peuvent se concentrer sur la gestion des environnements de production, l’infrastructure, la scalabilité, la supervision et enfin la garantie que les applications sont fournies correctement aux utilisateurs finaux, sans avoir à connaître le contenu des différents conteneurs. D’où le nom « conteneur », qui rappelle l’analogie avec les conteneurs de transport du monde réel. Par conséquent, les propriétaires du contenu d’un conteneur n’ont pas à se préoccuper de la façon dont le conteneur sera expédié, tandis que la société de transport achemine un conteneur de son point d’origine jusqu’à sa destination sans connaître le contenu ou sans s’y intéresser. De la même façon, les développeurs peuvent créer et posséder le contenu d’un conteneur Docker sans avoir à se préoccuper des mécanismes de « transport ».

Dans la colonne de gauche de la figure 2-1, les développeurs écrivent et exécutent le code localement dans des conteneurs Docker à l’aide de Docker pour Windows ou Mac. Ils définissent l’environnement d’exploitation pour le code à l’aide d’un fichier Dockerfile qui spécifie le système d’exploitation de base à exécuter, ainsi que les étapes de build pour la génération de leur code dans une image Docker. Les développeurs définissent la façon dont une ou plusieurs images interagiront à l’aide du manifeste de déploiement de fichier `docker-compose.yml` mentionné précédemment. Une fois qu’ils ont terminé leur développement local, ils poussent (push) leur code d’application en plus des fichiers de configuration Docker vers le dépôt de code de leur choix (autrement dit, le dépôt Git).

La colonne DevOps définit les pipelines de build/d’intégration continue (CI) à l’aide du fichier Dockerfile fourni dans le dépôt de code. Le système d’intégration continue (CI) extrait les images conteneur de base du registre Docker sélectionné et génère les images Docker personnalisées pour l’application. Les images sont alors validées et poussées (push) vers le registre Docker utilisé pour les déploiements sur plusieurs environnements.

Dans la colonne de droite, les équipes d’exploitation gèrent en production les applications et l’infrastructure déployées tout en supervisant l’environnement et les applications afin de pouvoir fournir des commentaires et des insights à l’équipe de développement sur la façon dont l’application peut être améliorée. Les applications de conteneur sont généralement exécutées en production à l’aide d’orchestrateurs de conteneurs comme [Kubernetes](https://kubernetes.io/), où généralement les [graphiques Helm](https://helm.sh/) sont utilisés pour configurer des unités de déploiement, au lieu de fichiers dockr-compose.

Les deux équipes collaborent par le biais d’une plateforme fondamentale (conteneurs Docker) qui fournit de manière contractuelle une séparation des responsabilités, tout en améliorant considérablement la collaboration des deux équipes dans le cycle de vie des applications. Les développeurs possèdent le contenu du conteneur, son environnement d’exploitation et ses interdépendances, tandis que les équipes d’exploitation prennent les images générées ainsi que le manifeste et les exécutent dans leur système d’orchestration.

## <a name="challenges-in-the-application-life-cycle-when-using-docker"></a>Défis dans le cycle de vie de l’application lors de l’utilisation de Dockr.

Nombreuses sont les raisons pour lesquelles le nombre d’applications conteneurisées augmentera dans les années à venir, et l’une d’elles est la création d’applications basées sur des microservices.

Au cours des 15 dernières années, l’utilisation de services Web a été la base de milliers d’applications et, au bout de quelques années, vous trouverez la même situation avec des applications basées sur des microservices qui s’exécutent sur des conteneurs d’ancrage.

Il est également important de mentionner que vous pouvez aussi utiliser des conteneurs Docker pour les applications monolithiques, auquel cas vous profitez toujours de la plupart des avantages de Docker. Les conteneurs ne ciblent pas uniquement des microservices.

L’utilisation de la conteneurisation de Docker et de microservices donne lieu à de nouveaux défis dans le processus de développement de vos organisations. Par conséquent, vous avez besoin d’une stratégie solide pour maintenir de nombreux conteneurs et microservices en cours d’exécution sur des systèmes de production. Finalement, les applications d’entreprise auront des centaines, voire des milliers de conteneurs/d’instances s’exécutant en production.

Ces défis créent de nouvelles demandes lors de l’utilisation des outils DevOps. vous devez donc définir de nouveaux processus dans vos activités DevOps et trouver des réponses pour les types de questions suivants :

- Quels outils puis-je utiliser pour le développement, l’intégration continue/le déploiement, la gestion et les opérations ?

- Comment mon entreprise peut gérer les erreurs dans des conteneurs lors de l’exécution en production ?

- Comment changer des parties de nos logiciels en production avec un temps d’arrêt minimal ?

- Comment puis-je mettre à l’échelle et surveiller notre système de production ?

- Comment pouvez-vous inclure le test et le déploiement des conteneurs dans notre pipeline de mise en version ?

- Comment utiliser des outils/plateformes open source pour les conteneurs dans Microsoft Azure ?

Si vous pouvez répondre à toutes ces questions, vous serez mieux préparé pour déplacer vos applications (existantes ou nouvelles) vers des conteneurs Docker.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Introduction à un workflow de cycle de vie d’application Docker de bout en bout générique

La figure 2-2 présente un workflow plus détaillé d’un cycle de vie d’application Docker, en s’intéressant particulièrement, dans cet exemple, à des activités et ressources DevOps spécifiques.

![Diagramme montrant le cycle de vie générique de bout en bout d’une application Dockr.](./media/containers-foundation-for-devops-collaboration/generic-end-to-enddpcker-app-life-cycle.png)

**Figure 2-2.** Workflow général du cycle de vie d’application conteneurisée Docker

Tout commence par le développeur, qui démarre l’écriture de code dans le workflow de la boucle interne. L’étape de la boucle interne est celle où les développeurs définissent tout ce qui se produit avant de pousser (push) le code vers le dépôt de code (par exemple, un système de gestion du code source comme Git). Une fois la validation effectuée, le dépôt déclenche l’intégration continue (CI) et le reste du workflow.

La boucle interne se compose d’étapes typiques telles que « code », « exécuter », « test » et « débogage », ainsi que les étapes supplémentaires nécessaires juste avant d’exécuter l’application localement. L’exécution et le test de l’application en tant que conteneur Docker font partie du processus du développeur. Le workflow de la boucle interne est expliqué dans les sections qui suivent.

En reprenant un moment pour examiner le flux de travail de bout en bout, le flux de travail DevOps est plus qu’une technologie ou un ensemble d’outils, il s’agit d’une mentalité qui nécessite une évolution culturelle. Il s’agit de personnes, de processus et des outils appropriés permettant rendre le cycle de vie de votre application plus rapide et plus prévisible. Les entreprises qui adoptent un workflow conteneurisé restructurent généralement leurs organisations pour représenter les personnes et les processus qui correspondent à des workflows conteneurisés.

L’utilisation de DevOps peut aider les équipes à répondre ensemble plus rapidement aux pressions concurrentielles en remplaçant les processus manuels sujets aux erreurs par une automatisation, ce qui se traduit par une meilleure traçabilité et des workflows reproductibles. Les organisations peuvent également gérer plus efficacement les environnements et réduire leurs coûts en combinant des ressources locales et cloud, ainsi que des outils solidement intégrés.

Quand vous implémenterez votre workflow DevOps pour les applications Docker, vous verrez que les technologies de Docker sont présentes à presque toutes les étapes du workflow, à partir de votre espace de développement quand vous travaillez dans la boucle interne (coder, exécuter, déboguer), la phase de build-test-CI et, enfin, le déploiement de ces conteneurs dans des environnements de préproduction et de production.

L’amélioration des pratiques concernant la qualité permettent d’identifier les erreurs tôt dans le cycle de développement, ce qui réduit les coûts liés à leur résolution. En incluant l’environnement et les dépendances dans l’image et en adoptant une philosophie du déploiement de la même image sur plusieurs environnements, vous encouragez une rigueur consistant à extraire les configurations spécifiques à l’environnement, ce qui rend les déploiements plus fiables.

Les données enrichies obtenues par le biais d’une instrumentation efficace (supervision et diagnostics) fournissent des insights sur les problèmes de performances et le comportement des utilisateurs pour orienter les futurs investissements et priorités.

DevOps doit être considéré comme un parcours, pas comme une destination. Il doit être implémenté de façon incrémentielle par le biais de projets bien délimités à partir desquels vous pouvez réussir, apprendre et évoluer.

## <a name="benefits-of-devops-for-containerized-applications"></a>Avantages de DevOps pour les applications conteneurisées

Voici quelques-uns des principaux avantages fournis par un workflow DevOps solide :

- Fournir des logiciels de meilleure qualité, plus rapides et offrant une meilleure conformité.

- Procéder à une amélioration et à des ajustements continus plus tôt et d’une manière plus rentable.

- Augmenter la transparence et la collaboration entre les parties prenantes impliquées dans la fourniture et l’exploitation des logiciels.

- Contrôler les coûts et utiliser plus efficacement les ressources provisionnées tout en réduisant les risques de sécurité.

- Affecter une connexion de type « plug and play » correcte à un grand nombre de vos investissements DevOps existants, notamment les investissements en open source.

>[!div class="step-by-step"]
>[Précédent](index.md) 
> [Suivant](../Microsoft-platform-tools-containerized-apps/index.md)
