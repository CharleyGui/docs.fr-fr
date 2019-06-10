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
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Quand déployer les conteneurs Windows sur Azure Container Service (Kubernetes)

Azure Container Service optimise la configuration des outils open source populaires et de technologies spécifiquement pour Azure. Vous obtenez une solution ouverte qui offre la portabilité pour vos conteneurs et la configuration de votre application. Vous sélectionnez la taille, le nombre d’hôtes et les outils d’orchestrator. Azure Container Service gère l’infrastructure pour vous.

Si vous travaillez déjà avec des orchestrateurs open source comme Kubernetes, Docker Swarm ou DC/OS, vous n’avez pas besoin de modifier vos pratiques de gestion pour déplacer des charges de travail de conteneur vers le cloud. Utiliser les outils de gestion d’application que vous êtes déjà familiarisé avec et se connecter via les points de terminaison d’API standards pour l’orchestrateur de votre choix.

Tous ces orchestrateurs sont des environnements matures si vous utilisez des conteneurs Linux Docker, mais pouvez être uniquement dans l’état d’aperçu pour les conteneurs Windows.

Par exemple, dans Kubernetes, prise en charge les conteneurs est natif (citoyen de première classe), à l’aide de conteneurs de Windows sur Kubernetes est également efficace (en version préliminaire dans ACS à compter du début 2018).

Remarque importante : L’évolution et « PaaS plus » version d’ACS (Azure Container Service) pour Kubernetes est AKS (Azure Kubernetes Service), les conteneurs Windows ne sont toujours pas pris en charge à compter du 2e trimestre 2018, toutefois, il sera bientôt possible.

>[!div class="step-by-step"]
>[Précédent](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Suivant](choosing-azure-compute-options-for-container-based-applications.md)
