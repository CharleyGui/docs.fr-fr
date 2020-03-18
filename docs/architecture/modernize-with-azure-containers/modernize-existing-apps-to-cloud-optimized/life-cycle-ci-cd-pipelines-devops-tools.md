---
title: Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Modernisez le cycle de vie de votre application avec les pipelines CI/CD et les outils DevOps dans le cloud
ms.date: 04/30/2018
ms.openlocfilehash: 17a78c108bfc61471128a34191ec7a5d7cc28289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503852"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="5d0a9-103">Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud</span><span class="sxs-lookup"><span data-stu-id="5d0a9-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="5d0a9-104">Les entreprises d’aujourd’hui doivent innover à un rythme rapide pour être concurrentielles sur le marché.</span><span class="sxs-lookup"><span data-stu-id="5d0a9-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="5d0a9-105">La fourniture d’applications modernes de haute qualité nécessite des outils et des processus DevOps essentiels pour mettre en œuvre ce cycle constant d’innovation.</span><span class="sxs-lookup"><span data-stu-id="5d0a9-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="5d0a9-106">Avec les bons outils DevOps, les développeurs peuvent rationaliser le déploiement continu et mettre plus rapidement les applications innovantes entre les mains des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5d0a9-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="5d0a9-107">Bien que les pratiques d’intégration et de déploiement continus soient bien établies, l’introduction de conteneurs introduit de nouvelles considérations, en particulier lorsque vous travaillez avec des applications multi conteneurs.</span><span class="sxs-lookup"><span data-stu-id="5d0a9-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="5d0a9-108">Azure DevOps Services prend en charge l’intégration continue et le déploiement d’applications multi-conteneurs dans une variété d’environnements grâce aux missions officielles de déploiement d’Azure DevOps Services :</span><span class="sxs-lookup"><span data-stu-id="5d0a9-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="5d0a9-109">Déploiement dans une application Web Azure pour conteneurs</span><span class="sxs-lookup"><span data-stu-id="5d0a9-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="5d0a9-110">Déploiement au service Azure Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5d0a9-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="5d0a9-111">Mais vous pouvez également vous déployer sur [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) ou DC/OS en utilisant les tâches basées sur le script Azure DevOps Services.</span><span class="sxs-lookup"><span data-stu-id="5d0a9-111">But you also can deploy to [Docker Swarm](https://blog.jcorioland.io/archives/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services.html) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="5d0a9-112">Pour continuer à faciliter l’agilité du déploiement, ces outils offrent d’excellentes expériences de déploiement de de développement à test à la production pour les charges de travail des conteneurs, avec un choix de solutions de développement et de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="5d0a9-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="5d0a9-113">La figure 4-12 montre un pipeline de déploiement continu qui se déploie à un cluster Kubernetes dans Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="5d0a9-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Capture d’écran du déploiement d’Azure DevOps Services sur un cluster Kubernetes.](./media/life-cycle-ci-cd-pipelines-devops-tools/deploy-mvc-app-container-kubernetes.png)

<span data-ttu-id="5d0a9-115">**Figure 4-12.**</span><span class="sxs-lookup"><span data-stu-id="5d0a9-115">**Figure 4-12.**</span></span> <span data-ttu-id="5d0a9-116">Le gazoduc de déploiement continu d’Azure DevOps Services, déployé dans un cluster Debernetes</span><span class="sxs-lookup"><span data-stu-id="5d0a9-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5d0a9-117">[Suivant précédent](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Next](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="5d0a9-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
