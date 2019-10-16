---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Choix de plateformes de calcul Azure pour les applications basées sur des conteneurs
ms.date: 05/04/2018
ms.openlocfilehash: 2262d2cf4e69e19e8b78c07c239602dd5dccc3cd
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318666"
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

![Figure 1](./media/image8.5.png)

> [!div class="step-by-step"]
> [Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
