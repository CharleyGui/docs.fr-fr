---
title: Étapes du workflow DevOps de la boucle externe pour une application Docker
description: Cycle de vie des applications Docker en conteneur avec la plateforme et les outils Microsoft
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644986"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a><span data-ttu-id="019be-103">Création de pipelines CI/CD dans Azure DevOps Services pour une application .NET Core 2.0 sur des conteneurs et déploiement sur un cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="019be-103">Creating CI/CD pipelines in Azure DevOps Services for a .NET Core 2.0 application on Containers and deploying to a Kubernetes cluster</span></span>

<span data-ttu-id="019be-104">Dans la Figure 5-12, vous pouvez voir le scénario de DevOps de bout en bout qui couvrent la gestion du code, la compilation de code, générer des images Docker, les images Docker push vers un Registre Docker et enfin le déploiement sur un cluster Kubernetes dans Azure.</span><span class="sxs-lookup"><span data-stu-id="019be-104">In Figure 5-12 you can see the end-to-end DevOps scenario covering the code management, code compilation, Docker images build, Docker images push to a Docker registry and finally the deployment to a Kubernetes cluster in Azure.</span></span>

![Flux de travail : Démarrage de l’ordinateur de développement.](media/docker-workflow-ci-cd-aks.png)

<span data-ttu-id="019be-107">**Figure 5-12**.</span><span class="sxs-lookup"><span data-stu-id="019be-107">**Figure 5-12**.</span></span> <span data-ttu-id="019be-108">Scénario CI/CD Création d’images Docker et le déploiement sur un cluster Kubernetes dans Azure</span><span class="sxs-lookup"><span data-stu-id="019be-108">CI/CD scenario creating Docker images and deploying to a Kubernetes cluster in Azure</span></span>

<span data-ttu-id="019be-109">Il est important de souligner que les deux pipelines, la build/CI et la mise en production et de livraison, sont connectés via le Registre Docker (par exemple, Docker Hub ou Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="019be-109">It is important to highlight that the two pipelines, build/CI, and release/CD, are connected through the Docker Registry (such as Docker Hub or Azure Container Registry).</span></span> <span data-ttu-id="019be-110">Le Registre Docker est une des principales différences par rapport à un processus CI/CD traditionnel sans Docker.</span><span class="sxs-lookup"><span data-stu-id="019be-110">The Docker registry is one of the main differences compared to a traditional CI/CD process without Docker.</span></span>

<span data-ttu-id="019be-111">Comme indiqué dans la Figure 5-13, la première phase est le pipeline de build/CI.</span><span class="sxs-lookup"><span data-stu-id="019be-111">As shown in Figure 5-13, the first phase is the build/CI pipeline.</span></span> <span data-ttu-id="019be-112">Dans les Services Azure DevOps, vous pouvez créer des pipelines de build/CI qui compiler le code, créez les images Docker et les envoient vers un Registre Docker comme Docker Hub ou Azure Container Registry.</span><span class="sxs-lookup"><span data-stu-id="019be-112">In Azure DevOps Services you can create build/CI pipelines that will compile the code, create the Docker images, and push them to a Docker Registry like Docker Hub or Azure Container Registry.</span></span>

![Affichage du navigateur de Azure DevOps, définition de tâche de processus de génération.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

<span data-ttu-id="019be-114">**Figure 5-13**.</span><span class="sxs-lookup"><span data-stu-id="019be-114">**Figure 5-13**.</span></span> <span data-ttu-id="019be-115">Pipeline de build/CI dans Azure DevOps création d’images Docker et lui envoyer des images vers un Registre Docker</span><span class="sxs-lookup"><span data-stu-id="019be-115">Build/CI pipeline in Azure DevOps building Docker images and pushing images to a Docker registry</span></span>

<span data-ttu-id="019be-116">La deuxième phase consiste à créer un pipeline de déploiement/mise en production.</span><span class="sxs-lookup"><span data-stu-id="019be-116">The second phase is to create a deployment/release pipeline.</span></span> <span data-ttu-id="019be-117">Dans les Services Azure DevOps, vous pouvez facilement créer un pipeline de déploiement ciblant un cluster Kubernetes à l’aide de tâches Kubernetes pour Azure DevOps Services, comme indiqué dans la Figure 5-14.</span><span class="sxs-lookup"><span data-stu-id="019be-117">In Azure DevOps Services, you can easily create a deployment pipeline targeting a Kubernetes cluster by using the Kubernetes tasks for Azure DevOps Services, as shown in Figure 5-14.</span></span>

![Affichage du navigateur de Azure DevOps, déployez à la définition de tâche de Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

<span data-ttu-id="019be-119">**Figure 5-14**.</span><span class="sxs-lookup"><span data-stu-id="019be-119">**Figure 5-14**.</span></span> <span data-ttu-id="019be-120">Pipeline de mise en production et de livraison dans le déploiement d’Azure DevOps Services sur un cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="019be-120">Release/CD pipeline in Azure DevOps Services deploying to a Kubernetes cluster</span></span>

> [! Procédure pas à pas]<span data-ttu-id="019be-121"> déploiement eShopModernized sur Kubernetes :</span><span class="sxs-lookup"><span data-stu-id="019be-121"> Deploying eShopModernized to Kubernetes:</span></span>
>
> <span data-ttu-id="019be-122">Pour une description détaillée des pipelines d’Azure DevOps CI/CD déploiement sur Kubernetes, consultez ce billet : \\</span><span class="sxs-lookup"><span data-stu-id="019be-122">For a detailed walkthrough of Azure DevOps CI/CD pipelines deploying to Kubernetes, see this post: \\</span></span>
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
><span data-ttu-id="019be-123">[Précédent](docker-application-outer-loop-devops-workflow.md)
>[Suivant](../run-manage-monitor-docker-environments/index.md)</span><span class="sxs-lookup"><span data-stu-id="019be-123">[Previous](docker-application-outer-loop-devops-workflow.md)
[Next](../run-manage-monitor-docker-environments/index.md)</span></span>
