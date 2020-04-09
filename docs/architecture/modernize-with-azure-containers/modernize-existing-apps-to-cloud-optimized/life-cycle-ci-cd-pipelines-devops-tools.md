---
title: Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Modernisez le cycle de vie de votre application avec les pipelines CI/CD et les outils DevOps dans le cloud
ms.date: 04/30/2018
ms.openlocfilehash: ac2d9a1e9ab432cf69cb3da670fc91c681f802c2
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987853"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a>Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud

Les entreprises d’aujourd’hui doivent innover à un rythme rapide pour être concurrentielles sur le marché. La fourniture d’applications modernes de haute qualité nécessite des outils et des processus DevOps essentiels pour mettre en œuvre ce cycle constant d’innovation. Avec les bons outils DevOps, les développeurs peuvent rationaliser le déploiement continu et mettre plus rapidement les applications innovantes entre les mains des utilisateurs.

Bien que les pratiques d’intégration et de déploiement continus soient bien établies, l’introduction de conteneurs introduit de nouvelles considérations, en particulier lorsque vous travaillez avec des applications multi conteneurs.

Azure DevOps Services prend en charge l’intégration continue et le déploiement d’applications multi-conteneurs dans une variété d’environnements grâce aux missions officielles de déploiement d’Azure DevOps Services :

- [Déploiement dans une application Web Azure pour conteneurs](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [Déploiement au service Azure Kubernetes](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

Mais vous pouvez également vous déployer sur [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) ou DC/OS en utilisant les tâches basées sur le script Azure DevOps Services.

Pour continuer à faciliter l’agilité du déploiement, ces outils offrent d’excellentes expériences de déploiement de de développement à test à la production pour les charges de travail des conteneurs, avec un choix de solutions de développement et de CI/CD.

La figure 4-12 montre un pipeline de déploiement continu qui se déploie à un cluster Kubernetes dans Azure Container Service.

![Capture d’écran du déploiement d’Azure DevOps Services sur un cluster Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

**Figure 4-12.** Le gazoduc de déploiement continu d’Azure DevOps Services, déployé dans un cluster Debernetes

>[!div class="step-by-step"]
>[Suivant précédent](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Next](migrate-to-hybrid-cloud-scenarios.md)
