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
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Quand déployer des conteneurs Windows sur Azure Container Service (autrement dit, Kubernetes)

Azure Container Service optimise la configuration d’outils et de technologies Open source populaires spécifiquement pour Azure. Vous bénéficiez d’une solution ouverte qui offre la portabilité à la fois pour vos conteneurs et pour la configuration de votre application. Vous sélectionnez la taille, le nombre d’hôtes et les outils Orchestrator. Azure Container Service gère l’infrastructure pour vous.

Si vous travaillez déjà avec des orchestrateurs Open source comme Kubernetes, Dockr essaim ou DC/OS, vous n’avez pas besoin de modifier vos pratiques de gestion existantes pour déplacer des charges de travail de conteneur vers le Cloud. Utilisez les outils de gestion d’applications que vous connaissez déjà et connectez-vous via les points de terminaison d’API standard pour l’orchestrateur de votre choix.

Tous ces orchestrateurs sont des environnements matures si vous utilisez des conteneurs d’ancrage Linux, mais qui peuvent uniquement être dans un état d’aperçu pour les conteneurs Windows.

Par exemple, dans Kubernetes, la prise en charge des conteneurs est native (citoyen de première classe). par conséquent, l’utilisation de conteneurs Windows sur Kubernetes est également efficace (en préversion dans ACS à compter des 2018 premières).

Remarque importante : la version évoluée et « plus PaaS » d’ACS (Azure Container Service) pour Kubernetes est AKS (service Kubernetes Azure). Toutefois, les conteneurs Windows ne sont toujours pas pris en charge à compter du 2018, mais ils seront bientôt pris en charge.

>[!div class="step-by-step"]
>[Précédent](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Suivant](choosing-azure-compute-options-for-container-based-applications.md)
