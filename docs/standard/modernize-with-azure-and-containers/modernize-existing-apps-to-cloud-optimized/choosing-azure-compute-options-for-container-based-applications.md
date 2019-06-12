---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser des applications .NET existantes avec des conteneurs de Cloud Azure et Windows | Choisir des plates-formes de calcul Azure pour les applications en conteneur
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66833856"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs

Comme vous l’avez remarqué après avoir lu les sections précédentes, Azure est un cloud ouverte qui offre plusieurs choix. Vous pouvez utiliser la mieux adaptée à vos besoins, toutefois, il met également en évidence questions sur les produits et technologies que vous devez utiliser pour vos applications en conteneur.

Comme un *par défaut* recommandation, ce qui suit est le principal critère recommandé dans ce guide :

- **Application monolithique unique :** Choisissez Azure App Service
- **Application multiniveau :** Choisissez des orchestrateurs tels que Azure Kubernetes Service (AKS) ou App Service si vous avez un seul ou plusieurs services back-end
- **Microservices :** Choisissez AKS ou Azure Web Apps for Containers
- **& Gestionnaires d’événements de fonctions sans serveur :** Choisissez Azure Functions
- **Lots à grande échelle :** Choisissez Azure Batch

Toutefois, cette recommandation à entreprendre avec une pincée de salt, comme la sélection du produit varie selon les besoins spécifiques de votre application et de caractéristiques. Pas toutes les applications sont les mêmes, même lorsque initialement, il peut présenter des types similaires.

Après une analyse plus approfondie des besoins de l’application, le produit sélectionné peut être différent. Mais, en tant que point de départ, il est judicieux d’avoir des recommandations initiales relatives à partir d’où vous pouvez commencer à évaluer et de test en fonction de certaine priorité.

Dans la figure suivante, vous pouvez voir une répartition des différents types d’applications et leurs Azure idéale scénarios d’hébergement.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
