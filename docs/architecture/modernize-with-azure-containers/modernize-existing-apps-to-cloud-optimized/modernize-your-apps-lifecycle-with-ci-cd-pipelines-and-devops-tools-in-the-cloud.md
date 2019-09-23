---
title: Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Moderniser le cycle de vie de votre application avec des pipelines CI/CD et des outils DevOps dans le Cloud
ms.date: 04/30/2018
ms.openlocfilehash: 4e4436ac4a622a82cc990b977b03eeae95ca9368
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181906"
---
# <a name="modernize-your-apps-lifecycle-with-cicd-pipelines-and-devops-tools-in-the-cloud"></a><span data-ttu-id="691ad-103">Moderniser le cycle de vie de votre application avec les pipelines d’intégration continue/de déploiement continu et les outils DevOps dans le cloud</span><span class="sxs-lookup"><span data-stu-id="691ad-103">Modernize your app's lifecycle with CI/CD pipelines and DevOps tools in the cloud</span></span>

<span data-ttu-id="691ad-104">Aujourd’hui, les entreprises doivent innover à un rythme rapide pour être compétitifs dans la place de marché.</span><span class="sxs-lookup"><span data-stu-id="691ad-104">Today’s businesses need to innovate at a rapid pace to be competitive in the marketplace.</span></span> <span data-ttu-id="691ad-105">La mise en place d’applications modernes de haute qualité requiert des outils et processus DevOps essentiels pour mettre en œuvre ce cycle constant d’innovation.</span><span class="sxs-lookup"><span data-stu-id="691ad-105">Delivering high-quality, modern applications requires DevOps tools and processes that are critical to implement this constant cycle of innovation.</span></span> <span data-ttu-id="691ad-106">Avec les outils DevOps appropriés, les développeurs peuvent simplifier le déploiement continu et obtenir des applications innovantes plus rapidement pour les mains des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="691ad-106">With the right DevOps tools, developers can streamline continuous deployment and get innovative applications into the hands of users more quickly.</span></span>

<span data-ttu-id="691ad-107">Bien que les pratiques d’intégration et de déploiement continues soient bien établies, l’introduction des conteneurs introduit de nouvelles considérations, en particulier lorsque vous travaillez avec des applications à plusieurs conteneurs.</span><span class="sxs-lookup"><span data-stu-id="691ad-107">Although continuous integration and deployment practices are well established, the introduction of containers introduces new considerations, particularly when you are working with multi-container applications.</span></span>

<span data-ttu-id="691ad-108">Azure DevOps Services prend en charge l’intégration et le déploiement continus d’applications à plusieurs conteneurs dans divers environnements via les tâches officielles de déploiement Azure DevOps Services :</span><span class="sxs-lookup"><span data-stu-id="691ad-108">Azure DevOps Services supports continuous integration and deployment of multi-container applications to a variety of environments through the official Azure DevOps Services deployment tasks:</span></span>

- [<span data-ttu-id="691ad-109">Déployer sur un Web App pour conteneurs Azure</span><span class="sxs-lookup"><span data-stu-id="691ad-109">Deploy to an Azure Web App for Containers</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-docker-webapp?tabs=dotnet-core)

- [<span data-ttu-id="691ad-110">Déployer dans le service Azure Kubernetes</span><span class="sxs-lookup"><span data-stu-id="691ad-110">Deploy to Azure Kubernetes Service</span></span>](https://docs.microsoft.com/azure/devops/pipelines/apps/cd/deploy-aks?tabs=dotnet-core)

<span data-ttu-id="691ad-111">Toutefois, vous pouvez également effectuer le déploiement sur un [essaimeur](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) ou DC/OS à l’aide de Azure DevOps services des tâches basées sur des scripts.</span><span class="sxs-lookup"><span data-stu-id="691ad-111">But you also can deploy to [Docker Swarm](https://blogs.msdn.microsoft.com/jcorioland/2016/11/29/full-ci-cd-pipeline-to-deploy-multi-containers-application-on-azure-container-service-docker-swarm-using-visual-studio-team-services/) or DC/OS by using Azure DevOps Services script-based tasks.</span></span>

<span data-ttu-id="691ad-112">Pour faciliter le déploiement, ces outils offrent une excellente expérience de déploiement de développement à la production pour les charges de travail de conteneur, avec un choix de solutions de développement et d’intégration continue/de déploiement continu.</span><span class="sxs-lookup"><span data-stu-id="691ad-112">To continue facilitating deployment agility, these tools provide excellent dev-to-test-to-production deployment experiences for container workloads, with a choice of development and CI/CD solutions.</span></span>

<span data-ttu-id="691ad-113">La figure 4-12 illustre un pipeline de déploiement continu qui se déploie sur un cluster Kubernetes dans Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="691ad-113">Figure 4-12 shows a continuous deployment pipeline that deploys to a Kubernetes cluster in Azure Container Service.</span></span>

![Azure DevOps Services pipeline de déploiement continu, déploiement sur un cluster Kubernetes](./media/image12.png)

<span data-ttu-id="691ad-115">**Figure 4-12.**</span><span class="sxs-lookup"><span data-stu-id="691ad-115">**Figure 4-12.**</span></span> <span data-ttu-id="691ad-116">Azure DevOps Services pipeline de déploiement continu, déploiement sur un cluster Kubernetes</span><span class="sxs-lookup"><span data-stu-id="691ad-116">Azure DevOps Services continuous deployment pipeline, deploying to a Kubernetes cluster</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="691ad-117">[Précédent](modernize-your-apps-with-monitoring-and-telemetry.md)
>[Suivant](migrate-to-hybrid-cloud-scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="691ad-117">[Previous](modernize-your-apps-with-monitoring-and-telemetry.md)
[Next](migrate-to-hybrid-cloud-scenarios.md)</span></span>
