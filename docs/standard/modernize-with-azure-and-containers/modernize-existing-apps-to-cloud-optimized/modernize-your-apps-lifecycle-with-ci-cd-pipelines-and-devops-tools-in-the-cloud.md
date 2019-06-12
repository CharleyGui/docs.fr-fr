---
title: Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Moderniser le cycle de vie de votre application avec les pipelines CI/CD et les outils DevOps dans le cloud
ms.date: 04/30/2018
ms.openlocfilehash: fb4bfab4a891e9c8a73867f18cb8249775f9b7b9
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833955"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud

Entreprises d’aujourd'hui doivent d’innover à un rythme rapide de compétitivité dans la place de marché. Applications modernes offrant de haute qualité, nécessite des outils de développement et les processus qui sont critiques pour implémenter ce cycle permanent de l’innovation. Avec les bons outils DevOps, les développeurs peuvent simplifier le déploiement continu et obtenir plus rapidement des applications innovantes dans les mains d’utilisateurs.

Bien que des pratiques de déploiement et d’intégration continues sont bien établies, l’introduction de conteneurs présente les considérations relatives à la nouvelle, en particulier lorsque vous travaillez avec des applications à plusieurs conteneurs.

Azure DevOps Services prend en charge l’intégration continue et déploiement d’applications à plusieurs conteneurs pour une variété d’environnements à travers les tâches de déploiement de Services de DevOps Azure officiels :

- [Déployer sur une application Web Azure pour les conteneurs](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [Déployer sur Azure Container Service – Kubernetes](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

Mais vous pouvez également déployer sur [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS à l’aide de tâches de script Azure DevOps Services.

Pour continuer ce qui facilite la souplesse de déploiement, ces outils fournissent excellent développement-test-production déploiement expériences pour les charges de travail de conteneur, en sélectionnant une option de développement et de solutions de CI/CD.

Figure 4-12 montre un pipeline de déploiement continu déploie sur un cluster Kubernetes dans Azure Container Service.

![Pipeline de déploiement continu DevOps Services Azure, le déploiement sur un cluster Kubernetes](./media/image12.png)

> **Figure 4-12.** Pipeline de déploiement continu DevOps Services Azure, le déploiement sur un cluster Kubernetes

>[!div class="step-by-step"]
>[Précédent](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Suivant](migrate-to-hybrid-cloud-scenarios.md)
