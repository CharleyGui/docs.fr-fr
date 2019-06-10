---
title: Quand déployer les conteneurs Windows sur Azure Container Service (Kubernetes)
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Quand déployer les conteneurs Windows sur Azure Container Service (Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758567"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="e7599-103">Quand déployer les conteneurs Windows sur Azure Container Service (Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="e7599-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="e7599-104">Azure Container Service optimise la configuration des outils open source populaires et de technologies spécifiquement pour Azure.</span><span class="sxs-lookup"><span data-stu-id="e7599-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="e7599-105">Vous obtenez une solution ouverte qui offre la portabilité pour vos conteneurs et la configuration de votre application.</span><span class="sxs-lookup"><span data-stu-id="e7599-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="e7599-106">Vous sélectionnez la taille, le nombre d’hôtes et les outils d’orchestrator.</span><span class="sxs-lookup"><span data-stu-id="e7599-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="e7599-107">Azure Container Service gère l’infrastructure pour vous.</span><span class="sxs-lookup"><span data-stu-id="e7599-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="e7599-108">Si vous travaillez déjà avec des orchestrateurs open source comme Kubernetes, Docker Swarm ou DC/OS, vous n’avez pas besoin de modifier vos pratiques de gestion pour déplacer des charges de travail de conteneur vers le cloud.</span><span class="sxs-lookup"><span data-stu-id="e7599-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="e7599-109">Utiliser les outils de gestion d’application que vous êtes déjà familiarisé avec et se connecter via les points de terminaison d’API standards pour l’orchestrateur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="e7599-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="e7599-110">Tous ces orchestrateurs sont des environnements matures si vous utilisez des conteneurs Linux Docker, mais pouvez être uniquement dans l’état d’aperçu pour les conteneurs Windows.</span><span class="sxs-lookup"><span data-stu-id="e7599-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="e7599-111">Par exemple, dans Kubernetes, prise en charge les conteneurs est natif (citoyen de première classe), à l’aide de conteneurs de Windows sur Kubernetes est également efficace (en version préliminaire dans ACS à compter du début 2018).</span><span class="sxs-lookup"><span data-stu-id="e7599-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="e7599-112">Remarque importante : L’évolution et « PaaS plus » version d’ACS (Azure Container Service) pour Kubernetes est AKS (Azure Kubernetes Service), les conteneurs Windows ne sont toujours pas pris en charge à compter du 2e trimestre 2018, toutefois, il sera bientôt possible.</span><span class="sxs-lookup"><span data-stu-id="e7599-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e7599-113">[Précédent](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Suivant](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="e7599-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
