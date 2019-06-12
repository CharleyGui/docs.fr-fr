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
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="5c367-103">Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud</span><span class="sxs-lookup"><span data-stu-id="5c367-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="5c367-104">Entreprises d’aujourd'hui doivent d’innover à un rythme rapide de compétitivité dans la place de marché.</span><span class="sxs-lookup"><span data-stu-id="5c367-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="5c367-105">Applications modernes offrant de haute qualité, nécessite des outils de développement et les processus qui sont critiques pour implémenter ce cycle permanent de l’innovation.</span><span class="sxs-lookup"><span data-stu-id="5c367-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="5c367-106">Avec les bons outils DevOps, les développeurs peuvent simplifier le déploiement continu et obtenir plus rapidement des applications innovantes dans les mains d’utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5c367-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="5c367-107">Bien que des pratiques de déploiement et d’intégration continues sont bien établies, l’introduction de conteneurs présente les considérations relatives à la nouvelle, en particulier lorsque vous travaillez avec des applications à plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="5c367-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="5c367-108">Azure DevOps Services prend en charge l’intégration continue et déploiement d’applications à plusieurs conteneurs pour une variété d’environnements à travers les tâches de déploiement de Services de DevOps Azure officiels :</span><span class="sxs-lookup"><span data-stu-id="5c367-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="5c367-109">Déployer sur une application Web Azure pour les conteneurs</span><span class="sxs-lookup"><span data-stu-id="5c367-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?view=azure-devops)

- [<span data-ttu-id="5c367-110">Déployer sur Azure Container Service – Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5c367-110">Deploy to Azure Container Service – Kubernetes</span></span>](https://docs.microsoft.com/azure/devops/build-release/apps/cd/azure/deploy-container-kubernetes)

<span data-ttu-id="5c367-111">Mais vous pouvez également déployer sur [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS à l’aide de tâches de script Azure DevOps Services.</span><span class="sxs-lookup"><span data-stu-id="5c367-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="5c367-112">Pour continuer ce qui facilite la souplesse de déploiement, ces outils fournissent excellent développement-test-production déploiement expériences pour les charges de travail de conteneur, en sélectionnant une option de développement et de solutions de CI/CD.</span><span class="sxs-lookup"><span data-stu-id="5c367-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="5c367-113">Figure 4-12 montre un pipeline de déploiement continu déploie sur un cluster Kubernetes dans Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="5c367-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Pipeline de déploiement continu DevOps Services Azure, le déploiement sur un cluster Kubernetes](./media/image12.png)

> <span data-ttu-id="5c367-115">**Figure 4-12.**</span><span class="sxs-lookup"><span data-stu-id="5c367-115">**Figure 4-12.**</span></span> <span data-ttu-id="5c367-116">Pipeline de déploiement continu DevOps Services Azure, le déploiement sur un cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5c367-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5c367-117">[Précédent](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Suivant](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="5c367-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
