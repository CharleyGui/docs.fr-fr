---
title: Créer des pipelines CI/CD dans Azure DevOps Services pour une application .NET sur des conteneurs et déploiement sur un cluster Kubernetes
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
ms.date: 01/06/2021
ms.openlocfilehash: ef994f132716547ee402237016ee71013528d779
ms.sourcegitcommit: 7ef96827b161ef3fcde75f79d839885632e26ef1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/07/2021
ms.locfileid: "97970484"
---
# <a name="create-cicd-pipelines-in-azure-devops-services-for-a-net-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Créer des pipelines CI/CD dans Azure DevOps Services pour une application .NET sur des conteneurs et déploiement sur un cluster Kubernetes

Dans la figure 5-12, vous pouvez voir le scénario DevOps de bout en bout couvrant la gestion du code, sa compilation, la création d’images Docker, leur poussée (push) vers un registre Docker et enfin le déploiement sur un cluster Kubernetes dans Azure.

![Workflow : démarre sur l’ordinateur de développement. La poussée (push) vers un dépôt commence la tâche de build/d’intégration continue (CI) à l’aide d’une image personnalisée qui est poussée vers un registre Docker, puis utilisée par la tâche de déploiement/CD pour finalement être poussée vers AKS.](media/docker-workflow-ci-cd-aks.png)

**Figure 5-12**. Scénario d’intégration continue/de déploiement continu (CI/CD) créant des images Docker et effectuant un déploiement sur un cluster Kubernetes dans Azure

Il est important de souligner que les deux pipelines (build/intégration continue et mise en production/déploiement continu) sont connectés par le biais du registre Docker (par exemple, Docker Hub ou Azure Container Registry). Le registre Docker est l’une des principales différences par rapport à un processus d’intégration continue/de déploiement continu (CI/CD) traditionnel sans Docker.

Comme indiqué dans la figure 5-13, la première phase est le pipeline de build/d’intégration continue. Dans Azure DevOps Services, vous pouvez créer des pipelines de build/d’intégration continue (CI) qui compile le code, créent les images Docker et les poussent (push) vers un registre Docker comme Docker Hub ou Azure Container Registry.

![Vue navigateur d’Azure DevOps : définition de la tâche Processus de génération.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Figure 5-13**. Pipeline de build/d’intégration continue dans Azure DevOps créant des images Docker et poussant (push) des images vers un registre Docker

La deuxième phase consiste à créer un pipeline de déploiement/mise en production. Dans Azure DevOps Services, vous pouvez facilement créer un pipeline de déploiement ciblant un cluster Kubernetes à l’aide de tâches Kubernetes pour Azure DevOps Services, comme indiqué dans la figure 5-14.

![Affichage, en mode Navigateur, d’Azure DevOps : définition de la tâche Déployer sur Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Figure 5-14**. Pipeline de mise en production/CD dans le déploiement d’Azure DevOps Services sur un cluster Kubernetes

> [!Procédure pas à pas] Déploiement d’eShopModernized sur Kubernetes :
>
> Pour obtenir une procédure pas à pas détaillée du déploiement de pipelines d’intégration continue/de déploiement continu (CI/CD) Azure DevOps sur Kubernetes, consultez le billet suivant : \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Précédent](docker-application-outer-loop-devops-workflow.md) 
> [Suivant](../run-manage-monitor-docker-environments/index.md)
