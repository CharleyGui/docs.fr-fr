---
title: Quand déployer des conteneurs Windows au service de conteneurs Azure (c’est-à-dire Kubernetes)
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Quand déployer des conteneurs Windows au service de conteneurs Azure (c’est-à-dire Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 3ff51a70d4e158b831155ab4992ec32f5d98cedb
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987762"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a>Quand déployer des conteneurs Windows au service de conteneurs Azure (c’est-à-dire Kubernetes)

Azure Container Service optimise la configuration des outils et technologies open source populaires spécifiquement pour Azure. Vous obtenez une solution ouverte qui offre la portabilité à la fois pour vos conteneurs et pour votre configuration d’application. Vous sélectionnez la taille, le nombre d’hôtes et les outils d’orchestrateur. Azure Container Service gère l’infrastructure pour vous.

Si vous travaillez déjà avec des orchestrateurs open-source comme Kubernetes, Docker Swarm ou DC/OS, vous n’avez pas besoin de modifier vos pratiques de gestion existantes pour déplacer les charges de travail des conteneurs vers le cloud. Utilisez les outils de gestion des applications que vous connaissez déjà et connectez via les paramètres standard de l’API pour l’orchestrateur de votre choix.

Tous ces orchestrateurs sont des environnements matures si vous utilisez des conteneurs Linux Docker, mais que vous n’êtes peut-être en état d’aperçu que pour Windows Containers.

Par exemple, à Kubernetes, le support pour les conteneurs est indigène (citoyen de première classe), donc l’utilisation de windows Containers sur Kubernetes est également efficace (en avant-première dans ACS au début de 2018).

Note importante: La version évoluée et "plus PaaS" d’ACS (Azure Container Service) pour Kubernetes est AKS (Azure Kubernetes Service), cependant, Windows Containers ne sont toujours pas pris en charge à partir du deuxième trimestre 2018, mais il sera pris en charge bientôt.

>[!div class="step-by-step"]
>[Suivant précédent](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Next](choosing-azure-compute-options-for-container-based-applications.md)
