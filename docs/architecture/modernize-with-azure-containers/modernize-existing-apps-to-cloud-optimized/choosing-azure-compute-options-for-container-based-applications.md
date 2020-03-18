---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser les applications .NET existantes avec les conteneurs Azure Cloud et Windows (fr) Choisir des plateformes de calcul Azure pour des applications basées sur des conteneurs
ms.date: 02/18/2020
ms.openlocfilehash: 52e7cf1c5dd3a5850564bdb33ac7a4ac4904f432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503889"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs

Comme vous l’avez remarqué après avoir lu les sections précédentes, Azure est un nuage ouvert qui offre plusieurs choix. Vous pouvez utiliser le meilleur ajustement pour vos besoins, cependant, il fait également surface des questions sur le produit / technologie que vous devriez utiliser pour vos applications conteneurisées.

Comme recommandation *par défaut,* voici les principaux critères recommandés dans les présentes directives :

- **Application monolithique unique :** Choisissez Azure App Service
- **Application N-Tier :** Choisissez des orchestrateurs tels que Azure Kubernetes Service (AKS) ou App Service si vous avez un seul ou quelques services back-end
- **Microservices:** Choisissez AKS ou Azure Web Apps pour les conteneurs
- **Fonctions sans serveur & les gestionnaires d’événements :** Choisissez Azure Functions
- **Lot à grande échelle:** Choisissez Azure Batch

Toutefois, cette recommandation doit être prise avec une pincée de sel, car la sélection du produit dépendra des besoins et des caractéristiques de votre application spécifique. Toutes les applications ne sont pas les mêmes, même lorsqu’au début, elles peuvent ressembler à des types similaires.

Après une analyse plus approfondie des besoins de l’application, le produit sélectionné pourrait être différent. Mais, comme point de départ, il est bon d’avoir des conseils initiaux d’où vous pouvez commencer à évaluer et à tester en fonction d’une certaine priorité.

Dans le tableau suivant, vous pouvez voir une ventilation de différents types d’applications et de leurs scénarios d’hébergement Azure possibles et recommandés.

| Architecture de l'application | VMs - Machines virtuelles Azure | ACI - Instances de conteneurs Azure | Azure App Service (w-w/o conteneurs) | AKS - Azure Kubernetes Services | Azure Functions | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Applications Web (Monolithique)**         | ![Possible avec les VM](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recommandé avec App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Possible avec AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **Applications N-Tier (Services)**        | ![Possible avec les VM](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recommandé avec App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Possible avec AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec Azure Fuctions](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Cloud-Native (Microservices)**  | | ![Possible avec ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![Recommandé avec AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Conteneurs Linux)&nbsp;| ![Recommandé avec Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Événement&#x2011;conduit) | |
| **Batch/Jobs (Tâches de fond)** | ![Possible avec les VM](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec App Service](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Possible avec AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Recommandé avec Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Tâches&nbsp;de fond) | ![Recommandé avec Azure Batch](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Grande échelle&#x2011;) |

**Légende**

![Icône recommandée](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Recommandé
![Icône possible](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Possible

> [!div class="step-by-step"]
> [Suivant précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
