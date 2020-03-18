---
title: Exécuter des applications composées et basées sur des microservices dans des environnements de production
description: Se familiariser avec les composants clés pour exécuter des applications basées sur des conteneurs en production
ms.date: 02/15/2019
ms.openlocfilehash: 69df3d39a00b91cbe59c96e5fcab841a60943bcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "68672916"
---
# <a name="run-composed-and-microservices-based-applications-in-production-environments"></a>Exécuter des applications composées et basées sur des microservices dans des environnements de production

Les applications composées de plusieurs microservices doivent être déployées dans des clusters orchestrateurs afin de simplifier la complexité du déploiement et le rendre viable du point de vue informatique. Sans cluster orchestrateur, il serait difficile de déployer une application de microservices complexes et d’en effectuer un scale-out.

## <a name="introduction-to-orchestrators-schedulers-and-container-clusters"></a>Introduction aux orchestrateurs, aux planificateurs et aux clusters de conteneurs

Précédemment dans ce livre électronique, les *clusters* et les *planificateurs* ont été introduites dans le cadre de la discussion sur l’architecture logicielle et le développement. Kubernetes et Service Fabric sont des exemples de clusters Docker. Ces deux orchestrateurs peuvent fonctionner au sein de l’infrastructure fournie par Microsoft Azure Kubernetes Service.

Quand les applications ont fait l’objet d’un scale-out sur plusieurs systèmes hôtes, la possibilité de gérer chaque système hôte et de masquer la complexité de la plateforme sous-jacente devient intéressante. C’est précisément ce que fournissent les orchestrateurs et les planificateurs. Examinons-les brièvement ici :

- **Planificateurs**.La « planification » fait référence à la capacité d’un administrateur à charger un fichier de service sur un système hôte qui définit la façon d’exécuter un conteneur spécifique. Le lancement de conteneurs dans un cluster Docker est généralement appelé « planification ». Même si la planification fait référence à l’acte spécifique de chargement de la définition de service, de manière plus générale, les planificateurs sont chargés du raccordement au système d’initialisation d’un hôte pour gérer les services, quelle que soit la capacité nécessaire.

   Un planificateur de cluster a plusieurs objectifs : utiliser efficacement les ressources du cluster, utiliser les contraintes de placement fournies par l’utilisateur, planifier rapidement les applications pour ne pas les laisser en état d’attente, avoir un certain degré d’« équité », être sensible aux erreurs et être toujours disponible.

- **Orchestrateurs**.Les plateformes étendent les fonctionnalités de gestion de cycle de vie aux charges de travail multiconteneurs complexes déployées sur un cluster d’hôtes. En faisant abstraction de l’infrastructure hôte, les outils d’orchestration permettent aux utilisateurs de traiter l’ensemble du cluster comme une cible de déploiement unique.

   Le processus d’orchestration implique des outils et une plateforme qui peuvent automatiser tous les aspects de la gestion des applications à partir du placement initial ou du déploiement par conteneur, le déplacement de conteneurs vers des hôtes différents en fonction de l’intégrité ou des performances de son hôte, la gestion des versions et le déploiement de mises à jour et de fonctions de supervision de l’intégrité qui prennent en charge la mise à l’échelle et le basculement, et bien plus encore.

   L’orchestration est un terme général qui fait référence à la planification de conteneurs à la gestion de clusters et éventuellement au provisionnement d’hôtes supplémentaires.

Le développement et la création intégrale des fonctionnalités fournies par les orchestrateurs et des planificateurs sont complexes. Par conséquent, vous voudrez généralement utiliser des solutions d’orchestration proposées par des fournisseurs.

>[!div class="step-by-step"]
>[Suivant précédent](index.md)
>[Next](manage-production-docker-environments.md)
