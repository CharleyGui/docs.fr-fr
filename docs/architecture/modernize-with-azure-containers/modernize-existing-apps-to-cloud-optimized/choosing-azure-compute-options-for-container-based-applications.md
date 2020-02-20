---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Choix de plateformes de calcul Azure pour les applications basées sur des conteneurs
ms.date: 02/18/2020
ms.openlocfilehash: 52e7cf1c5dd3a5850564bdb33ac7a4ac4904f432
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503889"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs

Comme vous l’avez remarqué après avoir lu les sections précédentes, Azure est un Cloud ouvert qui offre plusieurs choix. Vous pouvez utiliser la solution la mieux adaptée à vos besoins. Toutefois, elle présente également des questions sur le produit ou la technologie que vous devez utiliser pour vos applications en conteneur.

En guise de recommandation *par défaut* , les critères principaux recommandés dans ce guide sont les suivants :

- **Application monolithique unique :** Choisir Azure App Service
- **Application multiniveau :** Choisissez des orchestrateurs tels que le service Azure Kubernetes (AKS) ou App Service si vous avez un ou plusieurs services principaux
- **Microservices :** Choisir AKS ou Azure Web Apps pour les conteneurs
- **Fonctions sans serveur & gestionnaires d’événements :** Choisir Azure Functions
- **Lot à grande échelle :** Choisir Azure Batch

Toutefois, cette recommandation doit être prise avec un pincement Salt, car la sélection du produit dépend des besoins et caractéristiques de votre application spécifique. Toutes les applications ne sont pas les mêmes, même si elles peuvent sembler des types similaires.

Après une analyse plus poussée des besoins de l’application, le produit sélectionné peut être différent. Mais, comme point de départ, il est judicieux d’avoir des conseils initiaux à partir desquels vous pouvez commencer l’évaluation et le test en fonction de certaines priorités.

Dans le tableau suivant, vous pouvez voir une répartition de différents types d’applications et leurs scénarios d’hébergement Azure possibles et recommandés.

| Architecture de l'application | Machines virtuelles-machines virtuelles Azure | ACI-Azure Container Instances | Azure App Service (conteneurs w/o) | AKS-services Kubernetes Azure | Azure Functions | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Applications Web (monolithiques)**         | ![Possible avec les machines virtuelles](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recommandé avec App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Possible avec AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **Applications multicouches (services)**        | ![Possible avec les machines virtuelles](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recommandé avec App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Possible avec AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec Azure fuctions](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Cloud-natif (microservices)**  | | ![Possible avec ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![Recommandé avec AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Conteneurs de&nbsp;Linux)| ![Recommandé avec Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Piloté&#x2011;par les événements) | |
| **Traitement par lots/travaux (tâches en arrière-plan)** | ![Possible avec les machines virtuelles](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec App Service](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recommandé avec Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Tâches de&nbsp;d’arrière-plan) | ![Recommandé avec Azure Batch](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Grande&#x2011;échelle) |

**Légende**

![Icône recommandé](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Recommandations
![Icône possible](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Possible

> [!div class="step-by-step"]
> [Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
