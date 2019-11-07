---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Choix de plateformes de calcul Azure pour les applications basées sur des conteneurs
ms.date: 05/04/2018
ms.openlocfilehash: 079c9c5ca02b6dc75214d63cb59afdead03d3190
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737002"
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

Dans la figure 1, vous pouvez voir une répartition de différents types d’applications et de leurs scénarios d’hébergement Azure idéaux.

![Tableau des scénarios d’hébergement Azure les plus adaptés aux différentes applications.](./media/choosing-azure-compute-options-for-container-based-applications/azure-hosting-scenarios-for-apps.png)

> [!div class="step-by-step"]
> [Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
