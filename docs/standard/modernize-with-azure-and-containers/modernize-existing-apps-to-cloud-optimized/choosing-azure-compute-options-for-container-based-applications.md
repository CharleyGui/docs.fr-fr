---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Choisir des plates-formes de calcul Azure pour les applications en conteneur
ms.date: 05/04/2018
ms.openlocfilehash: d91cd279402dc24beb5f766c06cb85ac8d74f482
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758827"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs

Comme vous l’avez remarqué après avoir lu les sections précédentes, Azure est un cloud ouverte qui offre plusieurs choix. Vous pouvez utiliser la mieux adaptée à vos besoins, toutefois, il met également en évidence questions sur les produits et technologies que vous devez utiliser pour vos applications en conteneur.

Comme un *par défaut* recommandation, ce qui suit est le principal critère recommandé dans ce guide :

- **Application monolithique unique :** Choisissez Azure App Service
- **Application multiniveau :** Choisissez des orchestrateurs tels que Azure Kubernetes Service (AKS) ou App Service si vous avez un seul ou plusieurs services back-end
- **Microservices de Linux :** Choisissez AKS/Kubernetes
- **Microservices de Windows :** Choisissez Azure Web Apps for Containers
- **& Gestionnaires d’événements de fonctions sans serveur :** Choisissez Azure Functions
- **Lots à grande échelle :** Choisissez Azure Batch

Toutefois, cette recommandation à entreprendre avec une pincée de salt, comme la sélection du produit varie selon les besoins spécifiques de votre application et de caractéristiques. Pas toutes les applications sont les mêmes, même lorsque initialement, il peut présenter des types similaires.

Après une analyse plus approfondie des besoins de l’application, le produit sélectionné peut être différent. Mais, en tant que point de départ, il est judicieux d’avoir des recommandations initiales relatives à partir d’où vous pouvez commencer à évaluer et de test en fonction de certaine priorité.

Dans la figure suivante, vous pouvez voir une répartition des différents types d’applications et leurs Azure idéale scénarios d’hébergement.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
