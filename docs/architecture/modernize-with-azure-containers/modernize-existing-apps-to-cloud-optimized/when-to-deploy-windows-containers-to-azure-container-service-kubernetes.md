---
title: Quand déployer des conteneurs Windows au service de conteneurs Azure (c’est-à-dire Kubernetes)
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Quand déployer des conteneurs Windows au service de conteneurs Azure (c’est-à-dire Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69577942"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="2a0a9-103">Quand déployer des conteneurs Windows au service de conteneurs Azure (c’est-à-dire Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="2a0a9-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="2a0a9-104">Azure Container Service optimise la configuration des outils et technologies open source populaires spécifiquement pour Azure.</span><span class="sxs-lookup"><span data-stu-id="2a0a9-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="2a0a9-105">Vous obtenez une solution ouverte qui offre la portabilité à la fois pour vos conteneurs et pour votre configuration d’application.</span><span class="sxs-lookup"><span data-stu-id="2a0a9-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="2a0a9-106">Vous sélectionnez la taille, le nombre d’hôtes et les outils d’orchestrateur.</span><span class="sxs-lookup"><span data-stu-id="2a0a9-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="2a0a9-107">Azure Container Service gère l’infrastructure pour vous.</span><span class="sxs-lookup"><span data-stu-id="2a0a9-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="2a0a9-108">Si vous travaillez déjà avec des orchestrateurs open-source comme Kubernetes, Docker Swarm ou DC/OS, vous n’avez pas besoin de modifier vos pratiques de gestion existantes pour déplacer les charges de travail des conteneurs vers le cloud.</span><span class="sxs-lookup"><span data-stu-id="2a0a9-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="2a0a9-109">Utilisez les outils de gestion des applications que vous connaissez déjà et connectez via les paramètres standard de l’API pour l’orchestrateur de votre choix.</span><span class="sxs-lookup"><span data-stu-id="2a0a9-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="2a0a9-110">Tous ces orchestrateurs sont des environnements matures si vous utilisez des conteneurs Linux Docker, mais que vous n’êtes peut-être en état d’aperçu que pour Windows Containers.</span><span class="sxs-lookup"><span data-stu-id="2a0a9-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="2a0a9-111">Par exemple, à Kubernetes, le support pour les conteneurs est indigène (citoyen de première classe), donc l’utilisation de windows Containers sur Kubernetes est également efficace (en avant-première dans ACS au début de 2018).</span><span class="sxs-lookup"><span data-stu-id="2a0a9-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="2a0a9-112">Note importante: La version évoluée et "plus PaaS" d’ACS (Azure Container Service) pour Kubernetes est AKS (Azure Kubernetes Service), cependant, Windows Containers ne sont toujours pas pris en charge à partir du deuxième trimestre 2018, mais il sera pris en charge bientôt.</span><span class="sxs-lookup"><span data-stu-id="2a0a9-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2a0a9-113">[Suivant précédent](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Next](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="2a0a9-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
