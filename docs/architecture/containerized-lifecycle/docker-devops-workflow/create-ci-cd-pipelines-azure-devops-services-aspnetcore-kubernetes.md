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
# <a name="create-cicd-pipelines-in-azure-devops-services-for-a-net-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="188e0-103">Créer des pipelines CI/CD dans Azure DevOps Services pour une application .NET sur des conteneurs et déploiement sur un cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="188e0-103">Create CI/CD pipelines in Azure DevOps Services for a .NET application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="188e0-104">Dans la figure 5-12, vous pouvez voir le scénario DevOps de bout en bout couvrant la gestion du code, sa compilation, la création d’images Docker, leur poussée (push) vers un registre Docker et enfin le déploiement sur un cluster Kubernetes dans Azure.</span><span class="sxs-lookup"><span data-stu-id="188e0-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Workflow : démarre sur l’ordinateur de développement.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="188e0-107">**Figure 5-12**.</span><span class="sxs-lookup"><span data-stu-id="188e0-107">**Figure 5-12**.</span></span> <span data-ttu-id="188e0-108">Scénario d’intégration continue/de déploiement continu (CI/CD) créant des images Docker et effectuant un déploiement sur un cluster Kubernetes dans Azure</span><span class="sxs-lookup"><span data-stu-id="188e0-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="188e0-109">Il est important de souligner que les deux pipelines (build/intégration continue et mise en production/déploiement continu) sont connectés par le biais du registre Docker (par exemple, Docker Hub ou Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="188e0-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="188e0-110">Le registre Docker est l’une des principales différences par rapport à un processus d’intégration continue/de déploiement continu (CI/CD) traditionnel sans Docker.</span><span class="sxs-lookup"><span data-stu-id="188e0-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="188e0-111">Comme indiqué dans la figure 5-13, la première phase est le pipeline de build/d’intégration continue.</span><span class="sxs-lookup"><span data-stu-id="188e0-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="188e0-112">Dans Azure DevOps Services, vous pouvez créer des pipelines de build/d’intégration continue (CI) qui compile le code, créent les images Docker et les poussent (push) vers un registre Docker comme Docker Hub ou Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="188e0-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Vue navigateur d’Azure DevOps : définition de la tâche Processus de génération.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="188e0-114">**Figure 5-13**.</span><span class="sxs-lookup"><span data-stu-id="188e0-114">**Figure 5-13**.</span></span> <span data-ttu-id="188e0-115">Pipeline de build/d’intégration continue dans Azure DevOps créant des images Docker et poussant (push) des images vers un registre Docker</span><span class="sxs-lookup"><span data-stu-id="188e0-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="188e0-116">La deuxième phase consiste à créer un pipeline de déploiement/mise en production.</span><span class="sxs-lookup"><span data-stu-id="188e0-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="188e0-117">Dans Azure DevOps Services, vous pouvez facilement créer un pipeline de déploiement ciblant un cluster Kubernetes à l’aide de tâches Kubernetes pour Azure DevOps Services, comme indiqué dans la figure 5-14.</span><span class="sxs-lookup"><span data-stu-id="188e0-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Affichage, en mode Navigateur, d’Azure DevOps : définition de la tâche Déployer sur Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="188e0-119">**Figure 5-14**.</span><span class="sxs-lookup"><span data-stu-id="188e0-119">**Figure 5-14**.</span></span> <span data-ttu-id="188e0-120">Pipeline de mise en production/CD dans le déploiement d’Azure DevOps Services sur un cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="188e0-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> <span data-ttu-id="188e0-121">[!Procédure pas à pas] Déploiement d’eShopModernized sur Kubernetes :</span><span class="sxs-lookup"><span data-stu-id="188e0-121">[!Walkthrough] Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="188e0-122">Pour obtenir une procédure pas à pas détaillée du déploiement de pipelines d’intégration continue/de déploiement continu (CI/CD) Azure DevOps sur Kubernetes, consultez le billet suivant : </span><span class="sxs-lookup"><span data-stu-id="188e0-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: </span></span>\
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="188e0-123">[Précédent](docker-application-outer-loop-devops-workflow.md) 
> [Suivant](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="188e0-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
