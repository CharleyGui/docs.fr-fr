---
title: Quand déployer des conteneurs Windows sur Azure Container Service (autrement dit, Kubernetes)
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Quand déployer des conteneurs Windows sur Azure Container Service (autrement dit, Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/08/2019
ms.locfileid: "69577942"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="57d22-103">Quand déployer des conteneurs Windows sur Azure Container Service (autrement dit, Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="57d22-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="57d22-104">Azure Container Service optimise la configuration d’outils et de technologies Open source populaires spécifiquement pour Azure.</span><span class="sxs-lookup"><span data-stu-id="57d22-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="57d22-105">Vous bénéficiez d’une solution ouverte qui offre la portabilité à la fois pour vos conteneurs et pour la configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="57d22-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="57d22-106">Vous sélectionnez la taille, le nombre d’hôtes et les outils Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="57d22-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="57d22-107">Azure Container Service gère l’infrastructure pour vous.</span><span class="sxs-lookup"><span data-stu-id="57d22-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="57d22-108">Si vous travaillez déjà avec des orchestrateurs Open source comme Kubernetes, Dockr essaim ou DC/OS, vous n’avez pas besoin de modifier vos pratiques de gestion existantes pour déplacer des charges de travail de conteneur vers le Cloud.</span><span class="sxs-lookup"><span data-stu-id="57d22-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="57d22-109">Utilisez les outils de gestion d’applications que vous connaissez déjà et connectez-vous via les points de terminaison d’API standard pour l’orchestrateur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="57d22-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="57d22-110">Tous ces orchestrateurs sont des environnements matures si vous utilisez des conteneurs d’ancrage Linux, mais qui peuvent uniquement être dans un état d’aperçu pour les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="57d22-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="57d22-111">Par exemple, dans Kubernetes, la prise en charge des conteneurs est native (citoyen de première classe). par conséquent, l’utilisation de conteneurs Windows sur Kubernetes est également efficace (en préversion dans ACS à compter des 2018 premières).</span><span class="sxs-lookup"><span data-stu-id="57d22-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="57d22-112">Remarque importante : la version évoluée et « plus PaaS » d’ACS (Azure Container Service) pour Kubernetes est AKS (service Kubernetes Azure). Toutefois, les conteneurs Windows ne sont toujours pas pris en charge à compter du 2018, mais ils seront bientôt pris en charge.</span><span class="sxs-lookup"><span data-stu-id="57d22-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="57d22-113">[Précédent](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Suivant](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="57d22-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
