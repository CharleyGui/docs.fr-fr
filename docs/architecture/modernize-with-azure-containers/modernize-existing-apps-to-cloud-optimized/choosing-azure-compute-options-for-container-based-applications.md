---
title: Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs
description: Moderniser des applications .NET existantes avec des conteneurs Cloud et Windows Azure | Choix de plateformes de calcul Azure pour les applications basées sur des conteneurs
ms.date: 05/04/2018
ms.openlocfilehash: 64ae542e006bf7a5d7a0be08fe1cff9770552a77
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2019
ms.locfileid: "69578342"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Choix des plateformes de calcul Azure pour les applications basées sur des conteneurs

Comme vous l’avez remarqué après avoir lu les sections précédentes, Azure est un Cloud ouvert qui offre plusieurs choix. Vous pouvez utiliser la solution la mieux adaptée à vos besoins. Toutefois, elle présente également des questions sur le produit ou la technologie que vous devez utiliser pour vos applications en conteneur.

En guise de recommandation *par défaut* , les critères principaux recommandés dans ce guide sont les suivants:

- **Application monolithique unique:** Choisir Azure App Service
- **Application multiniveau:** Choisissez des orchestrateurs tels que le service Azure Kubernetes (AKS) ou App Service si vous disposez d’un seul ou de plusieurs services principaux
- **Microservices** Choisir AKS ou Azure Web Apps pour les conteneurs
- **Fonctions sans serveur & gestionnaires d’événements:** Choisir Azure Functions
- **Lot à grande échelle:** Choisir Azure Batch

Toutefois, cette recommandation doit être prise avec un pincement Salt, car la sélection du produit dépend des besoins et caractéristiques de votre application spécifique. Toutes les applications ne sont pas les mêmes, même si elles peuvent sembler des types similaires.

Après une analyse plus poussée des besoins de l’application, le produit sélectionné peut être différent. Mais, comme point de départ, il est judicieux d’avoir des conseils initiaux à partir desquels vous pouvez commencer l’évaluation et le test en fonction de certaines priorités.

Dans la figure suivante, vous pouvez voir une répartition de différents types d’applications et de leurs scénarios d’hébergement Azure idéaux.

![](./media/image8.5.png)

> [!div class="step-by-step"]
> [Précédent](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Suivant](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
